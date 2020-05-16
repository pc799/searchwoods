<script>
import { Col, Container, Row } from "sveltestrap";
import Card from './Card.svelte';
import Sidecard from './Sidecard.svelte';
import { movieId } from './stores.js';

let json;
let json2;
let json3;
let sidecardPkg;
let cardPkg;
let flag = 0;

$: (async function () {
    if (flag != $movieId) {
        flag = $movieId;
        //tmdb
        const apiUrl = `https://api.themoviedb.org/3/movie/${$movieId}?api_key=364fd4d942b460f61eb785588038ab54&append_to_response=videos`;
        const response = await fetch(apiUrl);
        json = await response.json();
        //omdb
        const apiUrl2 = `https://www.omdbapi.com/?i=${json.imdb_id}&apikey=f6aa67f5`;
        const response2 = await fetch(apiUrl2);
        json2 = await response2.json();
        //nyt
        const apiUrl3 = `https://api.nytimes.com/svc/movies/v2/reviews/search.json?query=${json.title}&opening-date=${json2.Year}-01-01;${json2.Year}-12-31&api-key=Apg06EOIJx513EEDffAJmijfjkh0w7I7`;
        const response3 = await fetch(apiUrl3);
        json3 = await response3.json();

        let Trailer = "";
        for (let i=0; i<json.videos.results.length; i++) {
            if (json.videos.results[i].type === "Trailer") {
                Trailer = `https://www.youtube.com/watch?v=${json.videos.results[i].key}`;
                break;
            }
        }
        if (Trailer.length == 0) {
            Trailer = `http://www.youtube.com/results?search_query=${json.title}+trailer`;
        }

        let Production = "";
        for(let i=0; i<json.production_companies.length; i++) {
            Production += json.production_companies[i].name + ", ";
        }
        if (Production.length != 0) {
            Production = Production.substring(0, Production.length - 2);
        }
        else {
            Production = json2.Production;
        }

        let Review = "";
        if (json3.num_results != 0) {
            Review = json3.results[0].summary_short;
        }
        else {
            Review = "N/A";
        }

        sidecardPkg = {
            image: `https://image.tmdb.org/t/p/w600_and_h900_bestv2/${json.poster_path}`,
            trailer: Trailer,
        };
        cardPkg = {
            title: json.original_title,
            rated: json2.Rated,
            date: json2.Year,
            genre: json2.Genre,
            length: json2.Runtime,
            IMDb: json2.imdbRating + "/10",
            synopsis: json.overview,
            cast: json2.Actors,
            director: json2.Director,
            studio: Production,
            review: Review,
        };
    }
    })();
</script>

<container>
<Row>
    <Col md="4">
        <Sidecard {...sidecardPkg}></Sidecard>
    </Col>
    <Col md="8">
        <Card {...cardPkg}></Card>
    </Col>
</Row>
</container>

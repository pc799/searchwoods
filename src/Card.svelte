<script>
export let title = undefined;
export let rated = undefined;
export let date = undefined;
export let genre = undefined;
export let length = undefined;
export let IMDb = undefined;
export let synopsis = undefined;
export let cast = undefined;
export let director = undefined;
export let studio = undefined;
export let review = undefined;
</script>

{#if title != undefined}
<div>
    <h1>{title}</h1>
    <p class="subtitle"><b style="border: 0.1rem solid gray">{rated}</b> {date} ‧ {genre} ‧ {length}</p>

    <p class="rating"><i class="fab fa-imdb fa-lg"></i> {IMDb}</p>

    <p>{synopsis}</p>

    <p><b>Cast:</b> {cast}</p>
    <p><b>Direction:</b> {director}</p>
    <p><b>Production:</b> {studio}</p><br/>

    <span><img src="images/nyt.png" alt="NYT"/>  <b>Review:</b></span>
    <p>{review}</p>
</div>
{:else}
<section>
    <span><i class="fas fa-circle-notch fa-spin"></i> Loading...</span>
</section>
{/if}

<style>
div {
    margin:5%;
    font-size: small;
}

@media only screen and (min-width: 768px) {
    /* For Desktop: */
    div {
        margin-top: 5%;
        margin-right: 10%;
        font-size: medium;
    }
}

h1 {
    font-family: Roboto;
    font-style: normal;
    font-weight: bold;
}

.rating {
    font-size: 1.5rem;
}

.subtitle {
    font-family: Roboto;
    font-style: normal;
    font-weight: 300;
}

section {
    position: fixed;
    left: 0;
    top: 10%;
    width: 100%;
    text-align: center;
}
</style>

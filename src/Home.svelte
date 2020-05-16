<script>
export let name;
</script>

<section>
    <h1>&#9886;{name}&#9887;</h1>
    <p>Minimal movie search</p>
</section>

<footer>
&copy; <a href="https://praveenraj.tech/" target="_blank" rel="noopener">Praveen Raj</a> ‧
Data provided by
<a href="https://developer.nytimes.com" target="_blank" rel="noopener">NYT</a>,
<a href="https://www.omdbapi.com" target="_blank" rel="noopener">OMDb</a>,
<a href="https://www.themoviedb.org" target="_blank" rel="noopener">TMDb</a>,
<a href="https://www.imdb.com" target="_blank" rel="noopener">IMDb</a>
</footer>

<style>
h1, p {
    text-align: center;
    vertical-align: middle;
}

h1 {
    margin-top: 40%;
}

footer {
    position: fixed;
    left: 0;
    bottom: 10%;
    width: 100%;
    text-align: center;
}
</style>
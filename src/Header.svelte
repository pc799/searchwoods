<script>
    import { Input, DropdownItem } from 'sveltestrap';
    import { movieId } from './stores.js';

    let query;

    let json;
    async function handleInput(event) {
        if (event.key === 'Enter') {
            movieId.set(1);
            const apiUrl = `https://api.themoviedb.org/3/search/movie?api_key=364fd4d942b460f61eb785588038ab54&query=${query}&page=1`;
            const response = await fetch(apiUrl);
            json = await response.json();
        }
    }

    function handleClick(id) {
        movieId.set(id);
        json = null;
    }
</script>

<div>
    <Input
        type="text"
        placeholder="&#9889; Search"
        bind:value={query} 
        on:keydown={handleInput}
        readonly={false} />
    {#if json}
        {#each json.results as movie}
            <DropdownItem
            style="margin-top: 1px"
            on:click={handleClick(movie.id)}
            >
                {movie.title} ({movie.release_date.substr(0,4)})
            </DropdownItem>
        {/each}
    {/if}
</div>
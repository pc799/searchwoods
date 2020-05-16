<script>
import { Row } from "sveltestrap";

export let image = undefined;
export let trailer = undefined;
</script>

{#if trailer != undefined}
<div>
    <Row>
        <img class="responsive" src={image} alt="Poster"/>
    </Row>
    <Row>
    <a href={trailer} target="_blank" rel="noopener"><i class="fab fa-youtube"></i> Play trailer on YouTube</a>
    </Row>
</div>
{/if}

<style>
div {
    display: block;
    margin:auto auto;
    width: 50%;
    margin-top:10%;
}
.responsive {
    object-fit: cover;
    width: 320px;
    height: 180px;
    border-radius: 10px;
}

@media only screen and (min-width: 768px) {
    /* For Desktop: */
    div {
        margin-left:30%;
        margin-top:15%;
    }

    .responsive {
        width: 100%;
        height: auto;
        max-width: 320px;
    }
}

a {
    margin:0 auto;
    margin-top: 5%;
    text-align:center;display:block;
}
</style>
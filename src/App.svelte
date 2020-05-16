<script>
	import { Col, Container, Row } from "sveltestrap";
	import Header from "./Header.svelte";
	import Body from "./Body.svelte";
	import Home from "./Home.svelte";
	import { movieId } from './stores.js';

	export let name;
</script>

<container>
<Row>
    <Col sm="12" md={{ size: 6, offset: 3 }}>
		<Header></Header>
	</Col>
</Row>
<Row>
	{#if $movieId == 1}
		<p></p>
	{:else if $movieId}
		<Body></Body>
	{:else}
		<Col sm="12" md={{ size: 6, offset: 3 }}>
			<Home name={name}></Home>
		</Col>
	{/if}
</Row>
</container>

<style>
:global(body) {
	overflow-x: hidden;
}
</style>


<script lang="ts">
	import { Col } from "@sveltestrap/sveltestrap";
	import Sbutton from "./UI/Sbutton.svelte";
	export let name:string = 'red';
	export let score:number = 20;
</script>


<Col md={{size: 6}} sm={{size:12}} style="border-style: dotted;" class="border-5 my-2 my-md-5 p-4 p-md-5 border-{name == 'red' ? 'danger':'primary'}">
	<h3 class="text-center"> Team {name ?? ''} : {score}</h3>
	<div class="d-flex justify-content-evenly align-items-center w-25 mx-auto mt-4">
		<Sbutton on:buttonClicked actionType='inc' bind:team={name} bind:score={score} block={false} color="success" title="+"/>
		<Sbutton on:buttonClicked actionType='dec' bind:team={name} bind:score={score} block={false} color="danger" title="-"/>
	</div>
</Col>


<style>

</style>

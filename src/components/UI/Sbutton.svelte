

<script lang="ts">
	import { Button } from '@sveltestrap/sveltestrap';
	import { createEventDispatcher } from 'svelte';
	export let actionType:'inc' | 'dec';
	export let score:number = 20;
	export let color:string = 'primary';
	export let block:boolean = false;
	export let title:string = 'button';
	export let team:string;
	let dispatcher = createEventDispatcher()

function performAction(){
	if(actionType == 'inc')
		score += 1;
	if(actionType =='dec')
		score -= 1;
	dispatcher('buttonClicked' , {[team]: score})
}

</script>



<Button on:click={performAction} {block} {color}>{title}</Button>



<style></style>

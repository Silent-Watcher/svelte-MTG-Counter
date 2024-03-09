<script lang="ts">
	 import { Button, Container, Row } from '@sveltestrap/sveltestrap';
	 import Team from './components/Team.svelte';
	 $: resultValue = '';
	 let teams: Set<string> = new Set();
	 let redScore : number = 20;
	 let blueScore : number = 20;
	function checkScore(e:CustomEvent):void{
		let winnerTeam : string = '';
		const team = Object.keys(e.detail)[0]
		const score = e.detail[team];
		teams.add(team);
		if(score == 0) {
			for (const selectedTeam of teams.values()) {
				if(selectedTeam != team){
					winnerTeam = selectedTeam as string;
				}
			}
			resultValue = `${winnerTeam} wins 🥳`
		}
	}

	function resetGame():void{
		resultValue = '';
		redScore = 20;
		blueScore = 20;
	}
</script>

<Container fluid>
	<Container>
		<Row>
			<h1 class="mt-5">MTG Counter App</h1>
		</Row>

		<Row>
			<Team on:buttonClicked={checkScore} name="red" bind:score={redScore}/>
			<Team on:buttonClicked={checkScore} name="blue" bind:score={blueScore}/>
		</Row>
		{#if resultValue.length > 0}
			<p>{resultValue}</p>
		{/if}
		<Row>
			<Button on:click={resetGame} block={true} color='warning' title="Reset Game">Reset Game</Button>
		</Row>

	</Container>
</Container>


<style>
	h1{
		text-align: center;
	}
</style>

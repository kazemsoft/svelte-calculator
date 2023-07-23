<script>
	import Button from './Button.svelte';
	import { firstNumber } from '../store.js';
</script>

<div id="keypad">
	<Button resetAC={true} class="grayer">
		{#if $firstNumber?.length}
			C
		{:else}
			AC
		{/if}
	</Button>
	<Button class="grayer">+/-</Button>
	<Button class="grayer">%</Button>
	<Button _operand="division" class="orange">÷</Button>
	<Button digit="7">7</Button>
	<Button digit="8">8</Button>
	<Button digit="9">9</Button>
	<Button _operand="times" class="orange">⨉</Button>
	<Button digit="4">4</Button>
	<Button digit="5">5</Button>
	<Button digit="6">6</Button>
	<Button _operand="minus" class="orange">-</Button>
	<Button digit="1">1</Button>
	<Button digit="2">2</Button>
	<Button digit="3">3</Button>
	<Button _operand="add" class="orange">+</Button>
	<Button digit="0" style="grid-column:span 2">0</Button>
	<Button>.</Button>
	<Button _equal={true} class="orange">=</Button>
</div>

<style>
	#keypad {
		flex: 1;
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-template-rows: repeat(5, 1fr);
		grid-gap: 1px;
		background: gray;
		border-radius: 0 0 8px 8px;
	}
</style>

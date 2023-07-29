<script>
	import Button from './Button.svelte';
	import { firstNumber, operand } from '../store.js';
</script>

<div id="keypad">
	<Button resetAC={true} class="grayer">
		{#if $firstNumber?.length}
			C
		{:else}
			AC
		{/if}
	</Button>
	<Button sideFunction="func1" class="grayer">±</Button>
	<Button sideFunction="func2" class="grayer">%</Button>
	<Button
		isSelected={$operand === 'division' ? true : false}
		_operand="division"
		class={$operand === 'division' ? `hasOperand orange` : `orange`}>÷</Button
	>
	<Button digit="7">7</Button>
	<Button digit="8">8</Button>
	<Button digit="9">9</Button>
	<Button
		isSelected={$operand === 'times' ? true : false}
		_operand="times"
		class={$operand === 'times' ? `hasOperand orange` : `orange`}>⨉</Button
	>
	<Button digit="4">4</Button>
	<Button digit="5">5</Button>
	<Button digit="6">6</Button>
	<Button
		isSelected={$operand === 'minus' ? true : false}
		_operand="minus"
		class={$operand === 'minus' ? `hasOperand orange` : `orange`}>-</Button
	>
	<Button digit="1">1</Button>
	<Button digit="2">2</Button>
	<Button digit="3">3</Button>
	<Button
		isSelected={$operand === 'add' ? true : false}
		_operand="add"
		class={$operand === 'add' ? `hasOperand orange` : `orange`}>+</Button
	>
	<Button digit="0" style="grid-column:span 2">0</Button>
	<Button dot={true}>.</Button>
	<Button class={$operand === 'equal' ? `hasOperand orange` : `orange`} _operand="equal">=</Button>
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

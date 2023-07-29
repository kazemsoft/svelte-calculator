<script>
	import Keypad from '$lib/components/Keypad.svelte';
	import ResultBar from '$lib/components/ResultBar.svelte';
	import { firstNumber, secondNumber, operand } from '../lib/store.js';

	function handleClickDigit(digit) {
		if ($firstNumber && $operand) {
			if (digit === '0' && $secondNumber * 1 <= 0) $secondNumber = $secondNumber;
			else $secondNumber = $secondNumber + digit;
		} else {
			if (digit === '0' && $firstNumber * 1 <= 0) $firstNumber = $firstNumber;
			else $firstNumber = $firstNumber + digit;
		}
	}
	function handleClickOperand(_operand) {
		if ($secondNumber) {
			if ($operand === 'add') {
				$firstNumber = $firstNumber * 1 + $secondNumber * 1;
				$secondNumber = '';
				$operand = _operand;
			} else if ($operand === 'minus') {
				$firstNumber = $firstNumber * 1 - $secondNumber * 1;
				$secondNumber = '';
				$operand = _operand;
			} else if ($operand === 'division') {
				$firstNumber = ($firstNumber * 1) / ($secondNumber * 1);
				$secondNumber = '';
				$operand = _operand;
			} else if ($operand === 'times') {
				$firstNumber = $firstNumber * 1 * ($secondNumber * 1);
				$secondNumber = '';
				$operand = _operand;
			}
		} else $operand = _operand;
	}
	function handleDot() {
		if ($operand) {
			$secondNumber += '.';
		} else $firstNumber += '.';
	}
	function onKeyDown(e) {
		if (e.keyCode >= 48 && e.keyCode <= 57) {
			handleClickDigit((e.keyCode - 48).toString());
		}
		e.keyCode === 42 && handleClickOperand('times');
		e.keyCode === 43 && handleClickOperand('add');
		e.keyCode === 45 && handleClickOperand('minus');
		e.keyCode === 47 && handleClickOperand('division');
		e.keyCode === 13 && handleClickOperand('equal');
		e.keyCode === 46 && handleDot();
	}
</script>

<div id="container">
	<ResultBar />
	<Keypad />
</div>
<svelte:window on:keypress|preventDefault={onKeyDown} />

<style>
	#container {
		width: 350px;
		aspect-ratio: 3/4;
		border: 1px solid #ccc;
		border-radius: 8px;
		display: flex;
		flex-flow: column nowrap;
	}
</style>

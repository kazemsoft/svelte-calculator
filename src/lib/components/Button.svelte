<script>
	import { firstNumber, secondNumber, operand } from '../store.js';
	export let digit = '';
	export let resetAC = false;
	export let _operand = '';
	export let sideFunction = '';
	export let dot = '';

	function handleClickDigit(digit) {
		if ($firstNumber && $operand) {
			if (digit === '0' && $secondNumber * 1 <= 0) $secondNumber = $secondNumber;
			else $secondNumber = $secondNumber + digit;
		} else {
			if (digit === '0' && $firstNumber * 1 <= 0) $firstNumber = $firstNumber;
			else $firstNumber = $firstNumber + digit;
		}
	}
	function handleResetAC() {
		$firstNumber = '';
		$secondNumber = '';
		$operand = '';
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
	function handleSideFunction(func) {
		if (func === 'func1') {
			if ($operand) {
				$secondNumber = -1 * $secondNumber;
			} else {
				$firstNumber = -1 * $firstNumber;
			}
		} else {
			if ($operand) {
				$secondNumber = ($secondNumber / 100) * $firstNumber;
			} else {
				$firstNumber = $firstNumber / 100;
			}
		}
	}
	function handleDot() {
		if ($operand) {
			$secondNumber += '.';
		} else $firstNumber += '.';
	}
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
	on:click={() =>
		digit
			? handleClickDigit(digit)
			: resetAC
			? handleResetAC()
			: _operand
			? handleClickOperand(_operand)
			: sideFunction
			? handleSideFunction(sideFunction)
			: dot
			? handleDot()
			: null}
	{...$$restProps}
>
	<slot />
</div>

<style>
	div {
		display: flex;
		justify-content: center;
		align-items: center;
		background: rgb(177, 177, 177);
		font-size: 22px;
		font-weight: 900;
		-webkit-user-select: none; /* Safari */
		-ms-user-select: none; /* IE 10 and IE 11 */
		user-select: none; /* Standard syntax */
	}
	div:active {
		background: lightgray !important;
	}
	div.orange:active {
		background: rgb(209, 136, 0) !important;
	}
	.orange {
		background: orange !important;
		color: #fff;
		font-size: 32px !important;
	}
	.grayer {
		background: rgb(155, 155, 155) !important;
		color: #fff;
		font-size: 32px !important;
	}
	.hasOperand {
		border: 1px solid #000 !important;
	}
</style>

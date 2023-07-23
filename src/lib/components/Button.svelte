<script>
	import { firstNumber, secondNumber, operand } from '../store.js';
	export let digit = '';
	export let resetAC = false;
	export let _operand = '';
	export let _equal = false;

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
	function handleClickEqual() {
		if ($secondNumber) {
			if ($operand === 'add') {
				$firstNumber = $firstNumber * 1 + $secondNumber * 1;
				$secondNumber = '';
				$operand = '';
			} else if ($operand === 'minus') {
				$firstNumber = $firstNumber * 1 - $secondNumber * 1;
				$secondNumber = '';
				$operand = '';
			} else if ($operand === 'division') {
				$firstNumber = ($firstNumber * 1) / ($secondNumber * 1);
				$secondNumber = '';
				$operand = '';
			} else if ($operand === 'times') {
				$firstNumber = $firstNumber * 1 * ($secondNumber * 1);
				$secondNumber = '';
				$operand = '';
			}
		}
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
			: _equal
			? handleClickEqual()
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
		border: 0;
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
</style>

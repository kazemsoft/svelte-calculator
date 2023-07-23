<script>
	import { firstNumber, secondNumber, operand } from '../store.js';
</script>

<input value={$secondNumber ? $secondNumber : $firstNumber ? $firstNumber : '0'} />

<style>
	input {
		height: 80px;
		border: 0;
		border-radius: 8px 8px 0 0;
		background: rgb(107, 107, 107) !important;
		direction: rtl;
		padding: 0 10px;
		font-size: 42px;
		color: #fff;
	}
</style>

<script>
	import Keypad from "$lib/components/Keypad.svelte";
import ResultBar from "$lib/components/ResultBar.svelte";

</script>
<div id="container">
	<ResultBar />
	<Keypad />
</div>

<style>
	#container {
		width:350px;
		aspect-ratio: 3/4;
		border: 1px solid #ccc;
        border-radius:8px;
		display: flex;
		flex-flow:column nowrap;
	}
</style>

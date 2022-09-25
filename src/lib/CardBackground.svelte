<script>
	import { svg_element } from "svelte/internal";
	import chip from "../assets/chip.svg";
	import wifi from "../assets/wifi.svg";

	export let settings;
</script>

<svg
	xmlns="http://www.w3.org/2000/svg"
	style="background-color: {settings.background_color}"
>
	<g /></svg
>
<img src={chip} class="chip" alt="" />
<img src={wifi} class="wifi" alt="" />

<style type="text/css">
	svg {
		width: 100%;
		height: auto;
		border-radius: 3mm;
		width: 31.5em;
		height: 20em;
		position: relative;
	}
	.chip {
		position: absolute;
		left: 35px;
		top: 85px;
		width: 60px;
	}
	.wifi {
		position: absolute;
		left: 445px;
		top: 40px;
		width: 25px;
	}
</style>

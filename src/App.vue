<script setup lang="ts">
import { ref } from "vue";

let headline = ref("Antenna Calculator");
let subtext = ref("");
let inputData: number | null = null;

function calculateWave(): number {
	const input = inputData;
	const waveValue = 468 / input;
	headline.value = `${waveValue.toFixed(3)} ft`;
	subtext.value = `${String((waveValue / 2).toFixed(3))} ft per element`;
	console.log(`${waveValue.toFixed(3)} ft`);
	inputData = null;
	return waveValue;
}
</script>

<template>
	<main class="container">
		<div class="card">
			<div class="headline">
				<h1>{{ headline }}</h1>
				<p>{{ subtext }}</p>
			</div>
			<div class="form-options">
				<input
					type="number"
					v-model="inputData"
					@keyup.enter="calculateWave()"
					autofocus
					placeholder="Input a frequency in MHz and press Enter to get the full width of a dipole antenna"
				/>
			</div>
		</div>
	</main>
</template>

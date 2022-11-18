<script lang="ts">
	import { arrayStore } from '@sveltering/custom-store';

	//Array store uses Proxy, but will only react to changes directly to the root array.
	//To react to any changes to any object/array in the store use proxyStore
	let numbers = arrayStore<number>();

	let currentNum = 1;

	let interval = setInterval(() => {
		numbers.value.push(currentNum++);
	}, 1000);

	$: if ($numbers.length === 5) {
		clearInterval(interval);
	}
</script>

{#each $numbers as number}
	{number} <br />
{/each}

<script lang="ts">
	import { proxyStore } from '@sveltering/custom-store';

	let numbers = proxyStore<string>({
		array: ['hello'],
		one: 'ONE',
		two: 'TWO',
		three: 'THREE'
	});

	setTimeout(() => {
		numbers.value.four = 'FOUR';
	}, 1000);

	setTimeout(() => {
		numbers.value.five = 'FIVE';
	}, 2000);
	setTimeout(() => {
		numbers.value.six = 'SIX';
	}, 3000);
	setTimeout(() => {
		numbers.value.array.push('world');
	}, 4000);

	$: console.log($numbers);
</script>

{#each Object.keys($numbers) as key}
	{key} : {$numbers[key]} <br />
{/each}

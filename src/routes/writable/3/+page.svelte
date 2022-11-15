<script lang="ts">
	import { writableStore } from '@sveltering/custom-store';

	function currentTime(): string {
		return new Date().toTimeString();
	}

	let time = writableStore<string>(currentTime());

	setInterval(() => {
		time.value = currentTime();
	}, 1000);

	time.subscribe((value) => {
		console.log('the time is ' + value);
	});
	time.subscribe((value) => {
		console.log('to repeat, the time is ' + value);
		console.log('');
	});

	setTimeout(() => {
		time.purge();
		console.log('Purged, store object obliterated :)');
		console.log(time);
	}, 5000);
</script>

<h1>{$time}</h1>

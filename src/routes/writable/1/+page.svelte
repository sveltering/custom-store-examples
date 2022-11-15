<script lang="ts">
	import { writableStore } from '@sveltering/custom-store';

	function currentTime(): string {
		return new Date().toTimeString();
	}

	let time = writableStore<string>(currentTime());

	setInterval(() => {
		time.value = currentTime();
		//can also use time.value as a getter to get current store value
	}, 1000);
</script>

<h1>{$time}</h1>

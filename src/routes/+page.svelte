<script lang="ts">
	import Gap from '$lib/components/Gap.svelte';
	import Meta from '$lib/components/Meta.svelte';
	import { analytics } from '$lib/firebase';
	import { Button } from 'carbon-components-svelte';
	import { logEvent } from 'firebase/analytics';
	import { onMount } from 'svelte';

	function handleCTA() {
		logEvent(analytics, 'click', { cta: 'saju' });
	}

	function handleAbout() {
		logEvent(analytics, 'click', { cta: 'about' });
	}

	onMount(() => {});
</script>

<Meta title="Saju Insights"></Meta>

<h1>Welcome to Saju Insights!</h1>
<Gap></Gap>

<p>
	Discover the ancient wisdom of Korean astrology and uncover the secrets of your destiny. Saju,
	also known as the Four Pillars of Destiny, uses your birth date and time to provide deep insights
	into your personality, career, relationships, and health. By understanding the unique interplay of
	the Five Elements in your life, you can make more informed decisions and achieve greater balance
	and harmony.
</p>
<Gap></Gap>

<Button href="/saju" on:click={handleCTA}>Start Your Saju Reading Now!</Button>
<Button kind="secondary" href="/about" on:click={handleAbout}>Learn More About Saju</Button>

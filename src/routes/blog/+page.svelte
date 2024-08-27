<script lang="ts">
	let posts = [
		{
			id: 1,
			title: 'Daily Saju Reading - June 10, 2024',
			date: 'June 10, 2024',
			excerpt: 'Today’s reading focuses on balance and harmony in your life...',
			content: `
				<p>Today’s reading focuses on balance and harmony in your life. The interaction between the Wood and Fire elements suggests a day of growth and creativity. It’s a good time to start new projects or make significant decisions. However, be mindful of potential conflicts, and strive to maintain a peaceful and cooperative attitude.</p>
				<p>The influence of the Earth element today indicates stability and groundedness. Take some time to reflect on your long-term goals and ensure that your actions align with your overall life path. Financial matters may also come to the forefront, so handle them with care and prudence.</p>
				<p>Overall, today is a day to embrace new opportunities while staying grounded and mindful of your actions. Use the positive energies to your advantage and navigate any challenges with grace and wisdom.</p>
			`
		},
		{
			id: 2,
			title: 'Understanding the Five Elements',
			date: 'June 9, 2024',
			excerpt: 'The Five Elements (Wood, Fire, Earth, Metal, Water) play a crucial role in saju...',
			content: `
				<p>The Five Elements (Wood, Fire, Earth, Metal, and Water) are fundamental to saju readings. Each element has its own characteristics and influences different aspects of your life. Understanding these elements can help you make sense of your saju reading and apply its insights to your daily life.</p>
				<p><strong>Wood:</strong> Represents growth, creativity, and expansion. It is associated with spring and new beginnings. People with a strong Wood element are often innovative and forward-thinking.</p>
				<p><strong>Fire:</strong> Symbolizes passion, energy, and transformation. Linked to summer, Fire brings warmth and dynamism. Those with a dominant Fire element are typically charismatic and action-oriented.</p>
				<p><strong>Earth:</strong> Stands for stability, nourishment, and grounding. Connected to late summer, Earth provides a solid foundation. Individuals with a strong Earth element are usually dependable and practical.</p>
				<p><strong>Metal:</strong> Denotes structure, discipline, and clarity. Associated with autumn, Metal is about refinement and efficiency. People with a pronounced Metal element are often organized and meticulous.</p>
				<p><strong>Water:</strong> Represents wisdom, intuition, and adaptability. Linked to winter, Water signifies fluidity and depth. Those with a dominant Water element are usually introspective and flexible.</p>
				<p>By understanding the interplay of these elements in your saju chart, you can gain deeper insights into your personality, strengths, and challenges.</p>
			`
		}
	];

	let selectedPost: { title: any; date: any; content: any } | null = null;

	function selectPost(post: { title: any; date: any; content: any } | null) {
		selectedPost = post;
	}
</script>

<h1>Saju8 Blog</h1>

{#if selectedPost}
	<article>
		<h2>{selectedPost.title}</h2>
		<p><em>{selectedPost.date}</em></p>
		{@html selectedPost.content}
		<button on:click={() => (selectedPost = null)}>Back to Blog</button>
	</article>
{:else}
	{#each posts as post}
		<article>
			<button on:click={() => selectPost(post)} style="cursor: pointer;">{post.title}</button>
			<p><em>{post.date}</em></p>
			<p>{post.excerpt}</p>
		</article>
	{/each}
{/if}

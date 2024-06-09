<main>
	<div>
		<slot></slot>
	</div>
</main>

<style>
	main {
		width: 100%;
		min-height: calc(100dvh - 12rem);
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	div {
		max-width: 1020px;
	}
</style>

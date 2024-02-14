<script>
	import Smooth from './Smooth.svelte';
</script>

<body>
  <Smooth>
    <section class="section">
		<strong>1</strong>
	</section>
	<section class="section">
		<strong>2</strong>
	</section>
	<section class="section">
		<strong>3</strong>
	</section>
	<section class="section">
		<strong>4</strong>
	</section>
	<section class="section">
		<strong>5</strong>
	</section>
  </Smooth>
	
</body>

<style>
	html,
	body {
		margin: 0;
		padding: 0;
	}

	main {
		width: 100%;
	}

	.section {
		box-sizing: border-box;
		width: 100%;
		height: 100vh;
		display: flex;
		align-items: center;
		justify-content: center;
		font-family: sans-serif;
		font-size: 4em;
		&:first-child {
			background-color: #ccc;
		}
		&:nth-child(2) {
			color: #efefef;
			background-color: #212121;
		}
		&:nth-child(3) {
			background-color: #888;
		}
		&:nth-child(4) {
			background-color: #f00;
		}
	}

	.all {
		width: 100vw;
		height: 100vh;
		z-index: 0;
		position: sticky;
		top: 0;
	}
</style>

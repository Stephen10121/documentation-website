<script type="ts">
	import { page } from '$app/stores';
	import { goto } from '$app/navigation';

	const selectDoc = (e: any) => {
		goto(e.target.value);
	};
</script>

<header>
	<a href="/"><h1>Developer</h1></a>
	<div class="paths">
		<a href="/" class="{$page.url.pathname === '/' ? 'true' : ''} route">Home</a>
		<a href="/about" class="{$page.url.pathname === '/about' ? 'true' : ''} route">About</a>
		{#if $page.url.pathname.includes('/documentation')}
			<div class="docul">
				<a href="/documentation" class="true route">Docs</a>
				<select on:change={selectDoc}>
					<option value="/documentation">Select Doc</option>
					<option value="/documentation/gruzauth">GruzAuth</option>
				</select>
			</div>
		{:else}
			<a href="/documentation" class="route">Docs</a>
		{/if}
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0 10px;
		height: 70px;
		width: 100vw;
		background-color: #f3f3f3;
	}

	.paths {
		display: flex;
		gap: 10px;
		align-items: center;
		justify-content: center;
	}

	.route {
		font-family: "Roboto", sans-serif;
		color: black;
		padding: 10px;
		border-radius: 5px;
	}

	h1 {
		color: black;
		font-family: 'Poppins', sans-serif;
		font-weight: bold;
	}
	
	select {
		border: 1px solid black;
		padding: 10px 5px;
		border-radius: 5px;
	}

	.true {
		background-color: #dfdfdf;
	}
</style>

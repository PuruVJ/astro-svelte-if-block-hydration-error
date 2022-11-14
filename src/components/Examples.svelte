<script lang="ts">
	import { slide } from 'svelte/transition';

	let expanded = false;

	$: console.log(expanded);
</script>

<section class="container">
	<button on:click={() => (expanded = !expanded)}>Toggle</button>

	{#if expanded}
		<section class="container options-examples" transition:slide={{ duration: 500 }}>
			<!-- Element needed for astro bug, astro puts this at the end of `.container` rather than at the right place -->
			<div class="hack" style="display: contents;">
				<slot />
			</div>
		</section>
	{/if}
</section>

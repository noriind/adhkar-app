<script>
	import {fade} from 'svelte/transition'
	let {dhikr, taps, ontap} = $props();
</script>

<div class="card" in:fade>
	<p class="arabic" dir="rtl" lang="ar">{dhikr.arabic}</p>
	<p class="translit">{dhikr.translit}</p>
	<p>{dhikr.translation}</p>
	<p class="small">{dhikr.source}</p>

	<button class="tap" onclick={ontap}>
		{taps} / {dhikr.count}
	</button>
</div>

<style>
	.card { margin: 1rem 0; padding: 1.5rem; border: 1px solid #ddd; border-radius: 12px; }
  .arabic { font-size: 1.8rem; line-height: 2; }
  .translit { font-style: italic; }
  .small { font-size: 0.85rem; color: #666; }
  .tap { width: 100%; padding: 1rem; font-size: 1.4rem; background: #2e7d5b; color: white; border: 0; border-radius: 8px; cursor: pointer; }
</style>
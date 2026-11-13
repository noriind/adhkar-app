<script>
	let {current, total} = $props();
	let percent = $derived((current / total) * 100);
</script>

<div class="bar">
	<div class="fill" 
		style="width: {percent}%">
	</div>
</div>

<p class="small">
	{Math.min(current + 1, total)} / {total}
</p>

<style>
	.bar { height: 6px; background: #ddd; border-radius: 3px; }
  .fill { height: 100%; background: #2e7d5b; border-radius: 3px; transition: width 0.3s; }
  .small { font-size: 0.85rem; color: #666; }
</style>

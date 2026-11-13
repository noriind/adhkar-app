<script>
  import { morning, evening } from './adhkar.js';
	import ProgressBar from './ProgressBar.svelte';
	import DhikrCard from './DhikrCard.svelte';
	import './App.css';

	let mode = $state(null);
  let index = $state(0);
  let taps = $state(0);

	let list = $derived(mode === 'evening' ? evening : morning);
  let current = $derived(list[index]);
  let finished = $derived(index >= list.length);

	function start(selected) {
		mode = selected;
		index = 0;
		taps = 0;
	}
	
  function tap() {
    taps++;
    if (taps >= current.count) next();
  }

  function next() {
    index++;
    taps = 0;
  }

  function prev() {
    if (index > 0) {
      index--;
      taps = 0;
    }
  }

  function backToStart() {
		mode = null;
    index = 0;
    taps = 0;
  }
</script>

<main>
	{#if mode === null}
  <h1>Adhkar</h1>
	<p>Choose which adhkar you want to read.</p>
		<div class="nav">
			<button onclick={() => start('morning')}>Morning Adhkar</button>
			<button onclick={() => start('evening')}>Evening Adhkar</button>
		</div>
	{:else}
		<h1>{mode === 'morning' ? 'Morning' : 'Evening' } Adhkar</h1>
  <ProgressBar current={index} total={list.length} />

  {#if finished}
    <p>Done. Jazakallahu khayran.</p>
		<button onclick={backToStart}>Back to start</button>
  {:else}
    {#key index}
      <DhikrCard dhikr={current} {taps} ontap={tap} />
    {/key}

    <div class="nav">
      <button onclick={prev} disabled={index === 0}>Previous</button>
      <button onclick={next}>Next</button>
    </div>
		{/if}	
  {/if}
</main>

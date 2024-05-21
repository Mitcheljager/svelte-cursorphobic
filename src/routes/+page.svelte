<script>
  import Cursorphobic from "$lib/Cursorphobic.svelte"

  let range = 200
  let multiplier = 0.1
  let size = 50
  let smoothing = 0.1

  let headerActiveIndexes = [2, 1, 0, 23, 22, 46, 68, 67, 66, 4, 26, 48, 70, 49, 28, 6, 8, 30, 52, 74, 75, 76, 31, 9, 10, 12, 34, 56, 78, 79, 80, 15, 16, 17, 38, 60, 82, 19, 41, 63, 85, 86, 87, 42, 20, 21]
</script>

<div class="wrapper">
	<div class="header">
		<h1><mark>Svelte</mark> Cursorphobic</h1>

    <div class="svelte-grid">
      {#each { length: 88 } as _, i}
        <Cursorphobic range="150" multiplier="0.1">
          <div class="element" class:bg-primary={headerActiveIndexes.includes(i)} />
        </Cursorphobic>
      {/each}
    </div>

    <p>A (very) lightweight component that makes elements afraid of your cursor. Used to easily create cute animations that react to your mouse.</p>

    <p><a href="https://github.com/Mitcheljager/svelte-cursorphobic">GitHub</a></p>
	</div>

	<div class="block">
		<h2>Installation</h2>

		<p>Install using Yarn or NPM.</p>

		<code class="well">
			yarn add <mark>svelte-cursorphobic</mark>
		</code>

		<code class="well">
			npm install --save <mark>svelte-cursorphobic</mark>
		</code>

		<p>Include the component in your app.</p>

		<code class="well">
			import <mark>Cursorphobic</mark> from "svelte-cursorphobic"
		</code>
	</div>

  <div class="block">
    <div class="range">
      <span>Range</span>
      <input type="range" bind:value={range} min="50" max="500" />
      {range}
    </div>

    <div class="range">
      <span>Multiplier</span>
      <input type="range" bind:value={multiplier} min="0.05" max="1" step="0.05" />
      {multiplier}
    </div>

    <div class="range">
      <span>Size</span>
      <input type="range" bind:value={size} min="10" max="100" />
      {size}
    </div>

    <div class="range">
      <span>Smoothing</span>
      <input type="range" bind:value={smoothing} min="0.01" max="1" step="0.01" />
      {smoothing}
    </div>

    <div class="grid mt-1" style:--size={size + 'px'}>
      {#each { length: 100 } as _}
        <Cursorphobic {range} {multiplier} {smoothing}>
          <div class="element" />
        </Cursorphobic>
      {/each}
    </div>
  </div>

	<div class="block">
		Made by <a href="https://github.com/Mitcheljager">Mitchel Jager</a>
	</div>
</div>

<style>
	:global(:root) {
		--primary: #ff3e00;
		--text-color: #444;
		--text-color-light: #999;
		--text-color-lightest: black;
		--border-color: #edf3f0;
		--bg-well: #f6fafd;
		--bg-body: #fff;
    --wrapper-max-width: 540px;
	}

	@media (prefers-color-scheme: dark) {
		:global(:root) {
			--text-color: #b7c0d1;
			--text-color-light: #8e99af;
			--text-color-lightest: white;
			--border-color: #363d49;
			--bg-well: #21242c;
			--bg-body: #16181d;
		}
	}

	:global(body) {
		padding: 0;
		margin: 0;
		background: var(--bg-body);
		color: var(--text-color);
		font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
	}

	h1 {
		margin: 0 0 1rem;
		color: var(--text-color-lightest);
	}

	h2 {
		margin: 3rem 0 1.5rem;
		color: var(--text-color-lightest);
	}

	code {
		display: block;
		margin-top: 1rem;
		color: var(--text-color-light);
		font-size: .75rem;
		line-height: 1.5em;
	}

	mark {
		background: none;
		color: var(--primary);
	}

	a {
		color: var(--primary);
	}

	p:first-child {
		margin-top: 0;
	}

  .svelte-grid {
    display: grid;
    grid-template-columns: repeat(22, 1fr);
    width: fit-content;
  }

  .svelte-grid .element {
    --size: calc(min(100vw - 2rem, var(--wrapper-max-width)) / 22);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(10, 1fr);
    width: fit-content;
  }

  .element {
    width: var(--size, 3rem);
    height: var(--size, 3rem);
    border-radius: 0.5rem;
    background: var(--border-color);
    box-shadow: inset 0 0 0 1px var(--bg-body);
  }

  .range {
    display: grid;
    grid-template-columns: 5rem 10rem 3rem;
    width: auto;
    gap: margin(1);
  }

	.well {
		padding: .35rem .5rem;
		border-radius: .5rem;
		border: 1px solid var(--border-color);
		background: var(--bg-well);
	}

	.header {
		margin: 6rem 0 0;
	}

	.wrapper {
		max-width: var(--wrapper-max-width);
		margin: 0 auto;
		padding: 0 1rem 6rem;
	}

	.block {
    display: block;
		padding: 3rem 0;
		border-bottom: 1px solid var(--border-color);
	}

	.description {
		margin-bottom: 1rem;
	}

	@media (min-width: 600px) {
		.description {
			margin-bottom: 0;
		}
	}

	.table {
		display: grid;
		grid-template-columns: 1fr 1fr 3fr;
		grid-gap: 1rem .5rem;
	}

	.table strong {
		color: var(--text-color);
	}

	.table code {
		margin-top: 0;
		line-height: 1.3rem;
	}

	.chart {
		margin-top: .5rem;
	}

	:global(.chart--responsive svg) {
		width: 100%;
		height: auto;
	}

	table {
		width: 100%;
		border: 1px solid var(--border-color);
		border-radius: .5rem;
		border-collapse: collapse;
		background: var(--bg-well);
		font-size: clamp(0.75rem, 3vw, 1rem);
		color: var(--text-color-light);
		font-style: italic;
	}

	table tr:nth-child(even) td {
		background: var(--bg-body);
	}

	table tr td,
	table tr th {
		border: 0;
		padding: 0.5rem 0 0.5rem 1rem;
		text-align: left;
	}

	table :global(svg) {
		max-width: 100%;
		height: auto;
	}

	table .label {
		color: var(--text-color);
		font-style: normal;
	}

  .bg-primary {
    background: var(--primary);
  }
</style>

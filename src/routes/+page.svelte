<script>
  import Cursorphobic from "$lib/Cursorphobic.svelte"

  let range = 200
  let multiplier = 0.1
  let size = 1
  let smoothing = 0.25

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
			yarn add <mark>svelte-cursorphobic</mark> --dev
		</code>

		<code class="well">
			npm install <mark>svelte-cursorphobic</mark> --save-dev
		</code>

		<p>Include the component in your app.</p>

		<code class="well">
			import <mark>Cursorphobic</mark> from "svelte-cursorphobic"
		</code>
	</div>

  <div class="block">
		<h2>Usage</h2>

    <p>The component is nothing but a wrapper to make <em>anything</em> cursorphobic. All you do is wrap an element in the component, and you're done!</p>

    <code class="well">
      &lt;<mark>Cursorphobic</mark>&gt;<br>
      &nbsp;&nbsp;&lt;div&gt;I am afraid of cursors!&lt;/div&gt;<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic>
        <div class="element">I am afraid of cursors!</div>
      </Cursorphobic>
    </div>
  </div>

  <div class="block">
    <p>To make multiple elements cursorphobic, you wrap each element inside their own component. Position is done via regular old css. It's just an element, style it however you want!</p>

    <code class="well">
      &lt;div style="..."&gt;&lt;<mark>Cursorphobic</mark>&gt;&lt;div /&gt;&lt;/<mark>Cursorphobic</mark>&gt;&lt;/div&gt;<br>
      &lt;div style="..."&gt;&lt;<mark>Cursorphobic</mark>&gt;&lt;div /&gt;&lt;/<mark>Cursorphobic</mark>&gt;&lt;/div&gt;<br>
      &lt;div style="..."&gt;&lt;<mark>Cursorphobic</mark>&gt;&lt;div /&gt;&lt;/<mark>Cursorphobic</mark>&gt;&lt;/div&gt;<br>
      &lt;div style="..."&gt;&lt;<mark>Cursorphobic</mark>&gt;&lt;div /&gt;&lt;/<mark>Cursorphobic</mark>&gt;&lt;/div&gt;<br>
    </code>

    <div class="holder">
      {#each [[20, 10], [30, 40], [5, 20], [50, 50], [25, 60], [60, 10], [70, 40], [40, 75], [80, 15], [85, 70]] as [left, top]}
        <div style="position: absolute; top: {top}%; left: {left}%;"><Cursorphobic><div class="element bg-primary" /></Cursorphobic></div>
      {/each}
    </div>
  </div>

  <div class="block">
    <p>Need a grid like the one at the top of the page? Svelte, along with some basic CSS, do the heavy lifting.</p>

    <code class="well">
      &lt;div class="grid"&gt;<br>
      &nbsp;&nbsp;&#123;#each &#123; length: 80 &#125; as _&#125;<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&lt;<mark>Cursorphobic</mark> range="150" multiplier="0.1"&gt;<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;div class="element" /&gt;<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&lt;/<mark>Cursorphobic</mark>&gt;<br>
      &nbsp;&nbsp;&#123;/each&#125; <br>
      &lt;/div&gt;<br>
      <br>
      .grid &#123;<br>
      &nbsp;&nbsp;display: grid;<br>
      &nbsp;&nbsp;grid-template-columns: repeat(20, 1fr);<br>
      &nbsp;&nbsp;width: fit-content;<br>
      &#125;
    </code>

    <br>

    <div class="svelte-grid">
      {#each { length: 88 } as _}
        <Cursorphobic range="150" multiplier="0.1">
          <div class="element" />
        </Cursorphobic>
      {/each}
    </div>
  </div>

  <div class="block">
		<h2>Properties</h2>

    <p>The component has 3 properties to how the element reacts to your cursor.</p>

    <h3>Range</h3>

    <p>The <code>range</code> property controls from how far away the component starts reacting to your cursor. (Defaults to 200)</p>

    <code class="well">
      &lt;<mark>Cursorphobic</mark> range="100"&gt;<br>
      &nbsp;&nbsp;...<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic range="100">
        <div class="element">100</div>
      </Cursorphobic>
    </div>

    <code class="well">
      &lt;<mark>Cursorphobic</mark> range="300"&gt;<br>
      &nbsp;&nbsp;...<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic range="300">
        <div class="element">300</div>
      </Cursorphobic>
    </div>

    <h3>Multiplier</h3>

    <p>The <code>multiplier</code> property controls how heavily an element reacts to your cursor. (Range from 0 to 1, defaults to 0.1)</p>

    <code class="well">
      &lt;<mark>Cursorphobic</mark> multiplier="0.02"&gt;<br>
      &nbsp;&nbsp;...<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic multiplier="0.02">
        <div class="element">0.02</div>
      </Cursorphobic>
    </div>

    <code class="well">
      &lt;<mark>Cursorphobic</mark> multiplier="0.5"&gt;<br>
      &nbsp;&nbsp;...<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic multiplier="0.5">
        <div class="element">0.5</div>
      </Cursorphobic>
    </div>

    <h3>Smoothing</h3>

    <p>The <code>smoothing</code> property controls how quickly an element moves relative to changes in your cursor. (Range from 0 to 1, defaults to 0.25)</p>

    <code class="well">
      &lt;<mark>Cursorphobic</mark> smoothing="0.05"&gt;<br>
      &nbsp;&nbsp;...<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic smoothing="0.05">
        <div class="element">0.05</div>
      </Cursorphobic>
    </div>

    <code class="well">
      &lt;<mark>Cursorphobic</mark> smoothing="1"&gt;<br>
      &nbsp;&nbsp;...<br>
      &lt;/<mark>Cursorphobic</mark>&gt;<br>
    </code>

    <div class="holder">
      <Cursorphobic smoothing="1">
        <div class="element">1</div>
      </Cursorphobic>
    </div>
  </div>

  <div class="block">
    <h2>Playground</h2>

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
      <span>Smoothing</span>
      <input type="range" bind:value={smoothing} min="0.01" max="1" step="0.01" />
      {smoothing}
    </div>

    <div class="range">
      <span>Size</span>
      <input type="range" bind:value={size} min="0.3" max="2" step="0.1" />
      {size}
    </div>

    <div class="playground mt-1" style:--size={size}>
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

  * {
    box-sizing: border-box;
  }

	h1 {
		margin: 0 0 1rem;
		color: var(--text-color-lightest);
	}

	h2 {
		margin: 3rem 0 1.5rem;
		color: var(--text-color-lightest);
	}

  h3 {
    margin: 2rem 0 1rem;
  }

	code {
		display: inline-block;
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

  .element {
    border-radius: 0.5rem;
    background: var(--border-color);
    box-shadow: inset 0 0 0 1px var(--bg-body);
    padding: 0.5rem;
  }

  .svelte-grid {
    display: grid;
    grid-template-columns: repeat(22, 1fr);
    width: fit-content;
  }

  .svelte-grid .element {
    --size: calc(min(100vw - 2rem, (var(--wrapper-max-width) - 2rem)) / 22);
    width: var(--size);
    height: var(--size);
  }

  .playground {
    display: grid;
    grid-template-columns: repeat(10, 1fr);
    width: fit-content;
    margin-top: 1rem;
  }

  .playground .element {
    width: calc(var(--size, 1) * min(100vw - 2rem, (var(--wrapper-max-width) - 2rem)) / 10);
    height: calc(var(--size, 1) * min(100vw - 2rem, (var(--wrapper-max-width) - 2rem)) / 10);
  }

  .range {
    display: grid;
    grid-template-columns: 5rem 10rem 3rem;
    width: auto;
    gap: 1rem;
  }

  .holder {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 150px;
    margin-top: 1rem;
    border-radius: 1rem;
    background: var(--bg-well);
  }

	.well {
    display: block;
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

  .bg-primary {
    background: var(--primary);
  }

  input[type="range"] {
    -webkit-appearance: none;
      appearance: none;
      background: transparent;
      cursor: pointer;
  }

  input[type="range"]:focus {
    outline: none;
  }

  input[type="range"]::-webkit-slider-runnable-track {
    background-color: var(--border-color);
    border-radius: 0.5rem;
    height: 0.5rem;
  }

  input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    margin-top: -0.75rem;
    background-color: var(--primary);
    height: 2rem;
    width: 1rem;
  }

  input[type="range"]:focus::-webkit-slider-thumb {
    border: 1px solid var(--border-color);
    outline: 3px solid var(--border-color);
    outline-offset: 0.125rem;
  }

  input[type="range"]::-moz-range-track {
    background-color: var(--border-color);
    border-radius: 0.5rem;
    height: 0.5rem;
  }

  input[type="range"]::-moz-range-thumb {
    border: none;
    border-radius: 50%;
    background-color: var(--primary);
    height: 1rem;
    width: 1rem;
  }

  input[type="range"]:focus::-moz-range-thumb {
    border: 1px solid var(--border-color);
    outline: 3px solid var(--border-color);
    outline-offset: 0.125rem;
  }
</style>

# Svelte Cursorphobic

[![npm version](https://badgen.net/npm/v/svelte-cursorphobic)](https://www.npmjs.com/package/svelte-cursorphobic)
[![npm downloads](https://badgen.net/npm/dt/svelte-cursorphobic)](https://www.npmjs.com/package/svelte-cursorphobic)
[![bundle size](https://img.shields.io/bundlephobia/minzip/svelte-cursorphobic)](https://bundlephobia.com/package/svelte-cursorphobic)

A (very) lightweight component that makes elements afraid of your cursor. Used to easily create cute animations that react to your mouse.

**Demo and Docs**: https://mitcheljager.github.io/svelte-cursorphobic/

### Installation

Install using Yarn or NPM.
```js
yarn add cursorphobic --dev
```
```js
npm install cursorphobic --save-dev
```

Include the component in your app.
```js
import Cursorphobic from "svelte-cursorphobic"
```
```svelte
<Cursorphobic>...<Cursorphobic>
```

## Usage

For detailed documentation and demos check out: [https://mitcheljager.github.io/svelte-cursorphobic/](https://mitcheljager.github.io/svelte-cursorphobic/)

### Properties

| Property | Default | Description |
---|---|---
range | 200 | Controls from how far away the component starts reacting to your cursor.
multiplier | 0.1 | Controls how heavily an element reacts to your cursor.
smoothing | 0.25 | Controls how quickly an element moves relative to changes in your cursor.

---
title: Getting references to things
---

## Why?

svelte-cubed abstracts over many three.js APIs and objects, initialising and updating things for you. This is great! It's convenient and is kind of the point of the library. However, sometimes you do need access to the underlying three.js objects that svelte-cubed creates. This is especially true if you're trying to

- implement something that svelte-cubed doesn't support out of the box yet, like raycasting
- integrate with another open source library, like cannon.js

## Accessing global objects

Call `getGlobalObjects` to access to the canvas, scene, renderer, camera, and controls:

```svelte
<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	const { canvas, scene, renderer, camera, controls } = SC.getGlobalObjects();
</script>
```

## Accessing component internal instances

All svelte-cubed components expose a binding which contains a reference to its internal three.js object. For example, to get a reference to a `THREE.Mesh`:

```svelte
<script>
	import * as THREE from 'three';
	import * as SC from 'svelte-cubed';

	let mesh: THREE.Mesh;
</script>

<SC.Mesh bind:mesh />
```

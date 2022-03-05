<script>
	import * as THREE from 'three';
	import { setup } from '../../utils/context.js';
	import { transform } from '../../utils/object.js';
	import * as defaults from '../../utils/defaults.js';

	/** @type {THREE.Group} */
	export let group;

	export let position = defaults.position;
	export let rotation = defaults.rotation;
	export let scale = defaults.scale;
	export let renderOrder = 0;

	const { root, self } = setup(new THREE.Group());
	group = self;

	$: {
		self.renderOrder = renderOrder;
		transform(self, position, rotation, scale);
		root.invalidate();
	}
</script>

<slot></slot>
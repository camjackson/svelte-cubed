<script>
	import * as THREE from 'three';
	import { setup } from '../../utils/context.js';

	/** @type {THREE.AnimationClip} */
	export let clip;

	export let time = 0;
	export let timeScale = 1;
	export let weight = 1;

	const { root, parent } = setup();

	/** @type {THREE.AnimationMixer} */
	export const mixer = new THREE.AnimationMixer(parent);

	/** @type {THREE.AnimationAction} */
	export let action;

	$: {
		action = mixer.clipAction(clip);
		action.play();

		// TODO uncache stuff
	}

	$: {
		action.weight = weight;

		mixer.timeScale = timeScale;
		mixer.setTime(time);

		root.invalidate();
	}
</script>


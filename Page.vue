<template>
	<div id="projects-app-wordle-container"></div>
	<Head title="Wordle" />
</template>

<script>
import mitt from 'mitt';

import { createApp } from 'vue'

import { store } from './store/store';
import App from './App.vue';

import { Link } from '@inertiajs/inertia-vue3';
import Toast from "vue-toastification";
import { Head } from '@inertiajs/inertia-vue3'
import Base from '@/Pages/Layout/Base.vue';

export default {
	components: {
		Head
	},
	mounted(){
		const emitter = mitt();
		this.app = createApp(App)
		.use(store)
		.use(Toast, {
			position: "top-center",
		});
		
		this.app.config.globalProperties.emitter = emitter;
		this.app.component('Link', Link);

		this.app.mount('#projects-app-wordle-container')
	},
	unmounted(){
		this.app.unmount();
	},

	data(){
		return {
			app: {},
		}
	},

	layout: Base,
}

</script>
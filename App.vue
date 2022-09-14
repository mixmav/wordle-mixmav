<template>
	<component :is="'style'">{{ css }}</component>
	<div class="main-game-container">

		<div class="menu-back-container">
			<Link href="/projects" class="a"><i class="fa fa-chevron-left"></i>Back</Link>
		</div>

		<transition name="opacity">
			<game-info-dialog v-show="gameInfoDialogVisible"></game-info-dialog>
		</transition>

		<game></game>
	</div>
</template>


<script>
import css from "./scss/app.scss?inline";
import { mapState } from 'vuex';
import Game from './components/Game.vue';
import GameInfoDialog from './components/GameInfoDialog.vue';

export default {
	components: {
		GameInfoDialog,
		Game,
	},
	mounted(){
	},
    data() {
        return {
			css: css,
		};
    },
	methods: {
	},
	computed: {
		...mapState('GameInfoDialog', {
			gameInfoDialogVisible: 'visible',
		}),
	}
}
</script>

<style lang="scss" scoped>

	@import "./scss/variables";

	.main-game-container {
		height: 100vh;
		background: $primary-color;
		overflow: auto;
		.main-page-content{
			position: relative;
			z-index: $zIndex-main-page-content;
		}

		.menu-back-container{
			position: absolute;
			left: 15px;
			top: 10px;
			a{
				font-size: .8em;
			}
		}
	}
</style>
<template>
	<div class="mainPage">
		<div class="mainPage__inner">
			<AppHeader class="mainPage__header" />
			<AppBanner class="mainPage__banner" />
			<MainFAQ class="mainPage__faq" />
			<MainNews />
		</div>
		<MainSubscribe class="mainPage__sub" />
		<AppFooter class="mainPage__footer" />
	</div>
</template>

<script>
import AppHeader from "@/components/appHeader/index.vue";
import AppBanner from "@/components/appBanner/index.vue";
import MainFAQ from "@/components/mainFAQ/index.vue";
import MainNews from "@/components/mainNews/index.vue";
import MainSubscribe from "@/components/mainSubscribe/index.vue";

import AppFooter from "@/components/appFooter/index.vue";

export default {
	name: "IndexPage",

	components: {
		AppHeader,
		AppBanner,
		MainFAQ,
		MainNews,
		MainSubscribe,
		AppFooter,
	},
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/styles/variables.scss";

.mainPage {
	&__inner {
		background: #0b0a0d;

		padding-bottom: 109px;

		@media (max-width: $media_md) {
			padding-bottom: 80px;
		}
	}

	&__banner {
		margin-bottom: 150px;

		@media (max-width: $media_md) {
			margin-bottom: 80px;
		}
	}

	&__faq {
		margin-bottom: 100px;

		@media (max-width: $media_md) {
			margin-bottom: 80px;
		}
	}

	&__sub {
		padding: 50px 15px 50px 15px;

		@media (max-width: $media_md) {
			padding-top: 30px;
		}
	}

	&__footer {
		padding: 50px 0 80px 0;

		@media (max-width: $media_md) {
			padding-top: 80px;
		}
	}
}
</style>

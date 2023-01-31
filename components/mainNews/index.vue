<template>
	<div class="news">
		<div class="news__inner">
			<h1 class="news__title h1 h1--white">
				Новости
			</h1>

			<div class="news__cardsList">
				<div
					v-for="(item, index) in newsList"
					:key="index"
					class="news__cardsListItem"
				>
					<div class="news__cardsInner">
						<nuxt-link
							class="news__cardsLinkImg"
							:to='item.link'
						>
							<img
								class="news__cardsImg"
								:src="item.img"
								:alt="item.title"
							>
						</nuxt-link>

						<div class="news__cardsInnerWrapper">
							<h2 class="news__cardsTitle tx516">
								{{item.title}}
							</h2>

							<p class="news__cardsDescr tx514">
								{{item.text}}
							</p>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "MainNews",

	data() {
		return {
			newsList: [
				{
					img: "/images/img1.jpg",
					link: "/",
					title: "Загловок",
					text: "ОписаниОписание Описание  Описание Описание Описание  Описаниее",
				},

				{
					img: "/images/img2.jpg",
					link: "/",
					title: "Загловок",
					text: "ОписаниОписание Описание  Описание Описание Описание  Описаниее",
				},

				{
					img: "/images/img3.jpg",
					link: "/",
					title: "Загловок",
					text: "ОписаниОписание Описание  Описание Описание Описание  Описаниее",
				},

				{
					img: "/images/img4.jpg",
					link: "/",
					title: "Загловок",
					text: "ОписаниОписание Описание  Описание Описание Описание  Описаниее",
				},

				{
					img: "/images/img5.jpg",
					link: "/",
					title: "Загловок",
					text: "ОписаниОписание Описание  Описание Описание Описание  Описаниее",
				},

				{
					img: "/images/img6.jpg",
					link: "/",
					title: "Загловок",
					text: "ОписаниОписание Описание  Описание Описание Описание  Описаниее",
				},
			],
		};
	},
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/styles/variables.scss";

.news {
	margin: 0 auto;
	padding: 0 11px;

	max-width: 1270px;

	@media (max-width: $media_md) {
		padding: 0 0 0 11px;
	}

	&__inner {
		max-width: 1240px;
	}

	&__title {
		margin-bottom: 30px;

		@media (max-width: $media_md) {
			margin-bottom: 20px;
		}
	}

	&__cardsList {
		display: grid;
		grid-template-columns: repeat(3, 2fr);
		gap: 50px 30px;

		@media (max-width: $media_md) {
			grid-auto-flow: column;
			overflow-x: scroll;
		}
	}

	&__cardsListItem {
		min-width: 200px;
	}

	&__cardsInner {
		display: grid;
		gap: 30px;
	}

	&__cardsImg {
		width: 100%;
		height: 264px;
	}

	&__cardsTitle {
		margin-bottom: 10px;
	}
}
</style>

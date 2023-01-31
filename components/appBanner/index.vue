<template>
	<div class="banner">
		<Swiper
			class="banner__swiper"
			:options="swiperOptions"
		>
			<SwiperSlide
				v-for="(item, index) in slideList"
				:key="index"
				class="banner__slide container"
			>
				<div class="banner__content">
					<h3 class="banner__title">
						{{item.title}}
					</h3>

					<img
						class="banner__img"
						:src="item.img"
						:alt="item.title"
					/>
				</div>
			</SwiperSlide>
		</Swiper>

		<div class="banner__controls">
			<button
				slot="button-prev"
				class="banner__btn banner__btn--prev"
			>
				<svgicon
					class="banner__icon-arrow banner__icon-arrow--prev"
					name="arrow"
				/>
			</button>

			<button
				slot="button-next"
				class="banner__btn banner__btn--next"
			>
				<svgicon
					class="banner__icon-arrow banner__icon-arrow--next"
					name="arrow"
				/>
			</button>
		</div>
	</div>
</template>

<script>
import { Swiper, SwiperSlide } from "vue-awesome-swiper";

export default {
	name: "AppBanner",
	components: {
		Swiper,
		SwiperSlide,
	},

	data() {
		return {
			swiperOptions: {
				autoplay: {
					delay: 3000,
					disableOnInteraction: false,
				},
				speed: 700,
				loop: true,
				centeredSlides: true,
				effect: "flipEffect",
				slidesPerView: "auto",
				spaceBetween: 4,

				navigation: {
					nextEl: ".banner__btn--next",
					prevEl: ".banner__btn--prev",
				},
				breakpoints: {
					1300: {
						slidesPerView: "auto",
						spaceBetween: -10,
					},
				},
			},

			slideList: [
				{
					img: "/images/mainBanner/img1.jpg",
					title: "Слайд 1",
				},
				{
					img: "https://via.placeholder.com/1450x750/4b0082/",
					title: "Слайд 2",
				},
				{
					img: "/images/mainBanner/img1.jpg",
					title: "Слайд 3",
				},
				{
					img: "https://via.placeholder.com/1450x750/22c/",
					title: "Слайд 4",
				},
			],
		};
	},
};
</script>

<style lang="scss" scoped>
.banner {
	&__swiper {
		margin-bottom: 55px;

		@media (max-width: $media_md) {
			margin-bottom: 20px;
		}
	}

	&__slide {
		height: 650px;

		@media (max-width: $media_md) {
			height: 450px;
		}
	}

	&__content {
		height: 100%;

		@media (max-width: $media_md) {
			max-height: 450px;
		}
	}

	&__title {
		font-family: "MPLUS1p";
		font-weight: 500;
		font-size: 80px;
		line-height: 85px;
		letter-spacing: -0.03em;

		position: absolute;

		left: 50px;
		top: 406px;

		z-index: 5;

		@media (max-width: $media_md) {
			font-size: 40px;

			left: 35px;
			top: 206px;
		}
	}

	&__img {
		position: relative;

		width: 100%;
		height: 100%;

		border-radius: 6px;

		@media (max-width: $media_md) {
			max-height: 450px;
		}
	}

	&__controls {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 32px;
	}

	&__btn {
		width: 100px;
		height: 40px;

		&:hover {
			.banner__icon-arrow {
				fill: #75ff77;
			}
		}
	}

	&__icon-arrow {
		width: 100px;

		fill: #ffffff;

		transition: 0.3s;

		&--prev {
			transform: rotate(180deg);
		}
	}
}
</style>

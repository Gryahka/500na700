<template>
	<header class="header">
		<div
			class="header__wrap"
			:class="{
			'header__wrap--scrolled' : scrolled
		}"
		>
			<div class="header__container container">
				<div class="header__inner">
					<nuxt-link
						class="header__logoLink"
						to="/"
					>
						<img
							class="header__logo"
							src="~/static/svg/logo1.svg"
							alt="logo"
						/>
					</nuxt-link>

					<ul class="header__menu menu">
						<li class="menu__menuItem menu__menuItem--dropDown">
							<div class="menu__link menu__link--dropDown">
								Пункт 1
							</div>

							<div class="menu__dropDown dropDown">
								<div class="dropDown__container container">
									<div class="dropDown__inner">
										<ul class="dropDown__list">
											<li class="dropDown__item ">
												<a
													class="dropDown__link"
													href="#"
												>
													Подпункт 1
												</a>
											</li>

											<li class="dropDown__item">
												<a
													class="dropDown__link"
													href="#"
												>
													Подпункт 2
												</a>
											</li>

											<li class="dropDown__item">
												<a
													class="dropDown__link"
													href="#"
												>
													Подпункт 3
												</a>
											</li>

											<li class="dropDown__item">
												<a
													class="dropDown__link"
													href="#"
												>
													Подпункт 4
												</a>
											</li>

											<li class="dropDown__item">
												<a
													class="dropDown__link"
													href="#"
												>
													Подпункт 5
												</a>
											</li>

										</ul>
									</div>
								</div>
							</div>
						</li>

						<li class="menu__menuItem">
							<a
								class="menu__link"
								href="#"
							>
								Пункт 2
							</a>
						</li>

						<li class="menu__menuItem">
							<a
								class="menu__link"
								href="#"
							>
								Пункт 3
							</a>
						</li>

						<li class="menu__menuItem">
							<a
								class="menu__link"
								href="#"
							>
								Пункт 4
							</a>
						</li>

						<li class="menu__menuItem">
							<a
								class="menu__link"
								href="#"
							>
								Пункт 5
							</a>
						</li>
					</ul>

					<button
						class="header__menuBtn menuBtn"
						:class="{
								'menuBtn--active' : burgerState
						}"
						@click="setBurgerState"
					>
						<div class="menuBtn__top"></div>
						<div class="menuBtn__center"></div>
						<div class="menuBtn__bottom"></div>
					</button>
				</div>
			</div>
		</div>

		<div
			class="header__fake"
			aria-hidden="true"
		/>

		<BurgerMenu
			:is-visible="burgerState"
			@setBurgerState="setBurgerState"
		/>
	</header>
</template>

<script>
import BurgerMenu from "~/components/ui/burgerMenu/index.vue";

export default {
	name: "AppHeader",

	components: {
		BurgerMenu,
	},

	data() {
		return {
			scrolled: false,
			burgerState: false,
		};
	},

	methods: {
		setBurgerState() {
			this.burgerState = !this.burgerState;

			if (this.burgerState) {
				document.body.style.overflow = "hidden";
			} else {
				document.body.style.overflow = "auto";
			}
		},
	},

	mounted() {
		window.addEventListener("scroll", () => {
			this.scrolled = window.scrollY > 50;
		});
	},
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/styles/variables.scss";

.header {
	position: relative;

	&__wrap {
		position: fixed;
		top: 0;
		right: 0;
		left: 0;
		z-index: 20;

		padding: 90px 0 50px;

		background: #0b0a0d;

		transition: 0.6s;

		@media (max-width: $media_md) {
			padding: 35px 0 60px;
		}

		&--scrolled {
			padding: 16px 0 16px;

			.menu__dropDown {
				bottom: -280px;
			}
		}
	}

	&__inner {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 20px;

		max-width: 690px;

		@media (max-width: $media_md) {
			max-width: 100%;
		}
	}

	&__logoLink {
		display: block;
	}

	&__menuBtn {
		@media (min-width: $media_md) {
			display: none;
		}
	}

	&__fake {
		height: 212px;

		@media (max-width: $media_md) {
			height: 150px;
		}
	}
}

.menuBtn {
	position: relative;

	width: 36px;
	height: 25px;

	&--active {
		.menuBtn__top {
			transform: rotate(45deg) translate(8px, 8px);
		}

		.menuBtn__center {
			transform: rotate(-45deg);
		}

		.menuBtn__bottom {
			display: none;
		}
	}

	&__top {
		position: absolute;
		top: 0;

		width: 100%;
		height: 3px;

		background: #ffffff;

		transition: 0.5s;
	}

	&__center {
		width: 100%;
		height: 3px;

		background: #ffffff;

		transition: 0.5s;
	}

	&__bottom {
		position: absolute;
		right: 0;
		bottom: 0;

		width: 18px;
		height: 3px;

		background: #ffffff;
	}
}

.menu {
	display: flex;
	gap: 30px;

	@media (max-width: $media_md) {
		display: none;
	}

	&__menuItem {
		cursor: pointer;

		&--dropDown {
			&:hover {
				.dropDown {
					opacity: 1;
					visibility: visible;
				}

				.menu__link--dropDown {
					&::before {
						background: #ffffff;
					}
				}
			}
		}
	}

	&__link {
		font-weight: 500;
		font-size: 16px;
		line-height: 24px;
		color: #ffffff;

		text-decoration: none;

		&:hover {
			color: #75ff72;
		}

		&--dropDown {
			position: relative;

			&:hover {
				color: #ffffff;
			}

			&::after {
				content: "";
				position: absolute;
				top: 20px;
				right: 0;
				left: 0;

				display: block;

				height: 33px;
			}

			&::before {
				content: "";

				position: absolute;
				right: 0;
				bottom: -20px;
				left: 0;

				display: block;

				height: 3px;

				background: transparent;

				transition: 0.3s;
			}
		}
	}

	&__dropDown {
		bottom: -252px;
	}
}

.dropDown {
	position: absolute;
	right: 0;
	left: 0;

	padding: 75px 0 90px;

	background: #0b0a0d;

	cursor: auto;

	opacity: 0;
	visibility: hidden;
	transition: 0.5s;

	&__inner {
		margin-left: 250px;
	}

	&__list {
		display: grid;
		grid-template-columns: max-content max-content;
		gap: 30px 140px;
	}

	&__link {
		text-decoration: none;

		&:hover {
			color: #75ff72;
		}
	}
}
</style>

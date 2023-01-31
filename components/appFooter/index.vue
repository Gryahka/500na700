<template>
	<footer class="footer">
		<div class="footer__inner container">
			<div class="footer__wrap">
				<div class="footer__info">
					<div class="footer__infoBottom">
						<p class="footer__subtitle tx516">Заголовок</p>

						<p class="footer__descr tx514">
							ОписаниОписание Описание Описание Описание Описание
							Описаниее
						</p>
					</div>

					<nuxt-link
						class="footer__infoLink"
						to="https://500na700.ru/"
					>
						<p class="footer__infoLinkText">500na700.ru</p>
					</nuxt-link>
				</div>

				<div class="footer__socialRow">
					<nuxt-link
						class="footer__socialLink"
						to="/"
					>
						<img
							class="footer__socialIcon"
							src="~/static/svg/VK.comiconsvg.svg"
							alt="vk"
						/>
					</nuxt-link>

					<nuxt-link
						class="footer__socialLink"
						to="/"
					>
						<img
							class="footer__socialIcon"
							src="~/static/svg/Facebookicon.svg"
							alt="vk"
						/>
					</nuxt-link>

					<nuxt-link
						class="footer__socialLink"
						to="/"
					>
						<img
							class="footer__socialIcon"
							src="~/static/svg/tiktokicon 1.svg"
							alt="vk"
						/>
					</nuxt-link>

					<nuxt-link
						class="footer__socialLink"
						to="/"
					>
						<img
							class="footer__socialIcon"
							src="~/static/svg/youtube.svg"
							alt="vk"
						/>
					</nuxt-link>
				</div>
			</div>
		</div>
	</footer>
</template>

<script>
export default {
	name: "AppFooter",
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/styles/variables.scss";

.footer {
	background: #312f35;

	&__wrap {
		display: grid;
		grid-auto-flow: column;
		gap: 40px;

		max-width: 726px;

		@media (max-width: $media_md) {
			grid-auto-flow: row;
		}
	}

	&__subtitle {
		margin-bottom: 10px;
	}

	&__descr {
		margin-bottom: 25px;
	}

	&__socialRow {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 30px;

		@media (max-width: $media_md) {
			display: flex;
			align-items: center;
			justify-content: center;
		}
	}
}
</style>

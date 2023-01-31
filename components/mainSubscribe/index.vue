<template>
	<div class="sub container">
		<div class="sub__inner">
			<h1 class="sub__title h1 h1--dark">Подпишись</h1>

			<div class="sub__info">
				<p class="sub__text tx416 tx416--20">
					Отправляем анонсы новых статей, выпусков и <br> трансляций
				</p>

				<div>
					<div class="sub__infoInner">
						<input
							class="sub__input customInput customInput--email"
							:class="{
								'customInput--error' : $v.email.$invalid && pressed
							}"
							v-model="$v.email.$model"
							type="email"
							placeholder="Email"
						>

						<input
							class="sub__input customInput customInput--date"
							:class="{
								'customInput--error' : $v.date.$invalid && pressed
							}"
							v-model="$v.date.$model"
							type="date"
						>

						<input
							class="sub__input--phone customInput customInput--tel"
							:class="{
								'customInput--error' : $v.phone.$invalid && pressed
							}"
							v-model="$v.phone.$model"
							type="tel"
							placeholder="Телефон"
							@input="validatePhone($event.target.value)"
						>

						<input
							class="sub__input customInput customInput--time"
							:class="{
								'customInput--error' : $v.time.$invalid && pressed
							}"
							v-model="$v.time.$model"
							type="time"
						>
					</div>

					<button
						class="sub__btn btn tx416 tx416__20"
						type="button"
						@click="submit"
					>
						Подписаться
					</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import {
	AsYouType,
	isValidPhoneNumber,
	validatePhoneNumberLength,
} from "libphonenumber-js";
import { validationMixin } from "vuelidate";

const { required, email } = require("vuelidate/lib/validators");

export default {
	name: "MainSubscribe",
	mixins: [validationMixin],

	validations: {
		email: {
			required,
			email,
		},
		date: {
			required,
		},
		time: {
			required,
		},
		phone: {
			required,
		},
	},
	data() {
		return {
			pressed: false,

			email: "",
			phone: "",
			oldPhone: "",
			phoneValid: "",
			date: "",
			time: "",
		};
	},
	methods: {
		validatePhone(value) {
			const asYouType = new AsYouType("RU");
			const curPhone = asYouType.input(value);

			if (
				validatePhoneNumberLength(curPhone) !== "TOO_LONG" &&
				validatePhoneNumberLength(curPhone) !== "INVALID_COUNTRY" &&
				validatePhoneNumberLength(curPhone) !== "INVALID_LENGTH"
			) {
				this.phone = curPhone;
				this.oldPhone = curPhone;
				if (
					!asYouType.isInternational(this.phone) &&
					this.phone !== "+" &&
					this.phone !== ""
				) {
					this.phone = `+${this.phone}`;
					this.oldPhone = `+${this.phone}`;
				}
			} else {
				this.phone = this.oldPhone;
			}
			this.phoneValid = isValidPhoneNumber(this.phone, "RU");
		},

		async submit() {
			this.$v.$touch();
			this.pressed = true;

			if (!this.$v.$invalid && this.phoneValid) {
				this.pressed = true;

				alert("Валидация прошла успешно. Данные отправленны на сервер");
			}
		},
	},
};
</script>

<style lang="scss" scoped>
.sub {
	background: #ffffff;

	&__inner {
		max-width: 1240px;
	}

	&__title {
		margin-bottom: 30px;

		@media (max-width: $media_md) {
			margin-bottom: 20px;
		}
	}

	&__text {
		margin-bottom: 15px;

		@media (max-width: $media_md) {
			margin-bottom: 20px;

			br {
				display: none;
			}
		}
	}

	&__infoInner {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 20px;

		max-width: 820px;

		@media (max-width: $media_md) {
			grid-template-columns: repeat(1, 1fr);
			gap: 10px;
		}
	}

	&__input {
		&--phone {
			@media (max-width: $media_md) {
				grid-row: 2;
			}
		}
	}

	&__btn {
		margin-top: 20px;

		@media (max-width: $media_md) {
			margin-top: 10px;
		}
	}
}

.customInput {
	position: relative;

	padding: 14px 15px 16px 20px;

	height: 50px;

	border: 1px solid rgba(0, 0, 0, 0.4);
	border-radius: 10px;

	font-family: "MPLUS1p";
	font-weight: 400;
	font-size: 14px;
	line-height: 20px;
	color: rgba(0, 0, 0, 0.6);

	transition: 0.3s;

	&:focus {
		border: 1px solid #000000;

		color: #0b0a0d;
	}

	&:not(:placeholder-shown) {
		color: #0b0a0d;
	}

	&::-webkit-calendar-picker-indicator {
		display: none;
	}

	&--error {
		border-color: tomato;
	}
}
</style>

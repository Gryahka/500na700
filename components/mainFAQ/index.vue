<template>
	<div class="faq container">
		<div class="faq__inner">
			<h1 class="faq__title h1 h1--white">FAQ</h1>

			<div class="faq__list">
				<template v-for="(item, index) in accordionList">
					<CustomAccordion
						ref="fAccordion"
						:key="index"
						:isOpenProps="currentAccordion === index"
						class="faq__accordion"
						@click.native="setOpenedAccordion(index)"
					>
						<template slot="head">
							<div class="faq__accordionHeadRow">
								<p class="faq__accordionHead h2">
									{{ item.head }}
								</p>
							</div>
						</template>

						<template slot="body">
							<div
								class="faq__tx-wrap tx416 tx416--24"
								v-html="item.body"
							/>
						</template>
					</CustomAccordion>
				</template>
			</div>
		</div>
	</div>
</template>

<script>
import CustomAccordion from "/components/ui/customAccordion/index.vue";

export default {
	name: "MainFAQ",

	components: {
		CustomAccordion,
	},

	data() {
		return {
			currentAccordion: 0,

			accordionList: [
				{
					head: "Как добраться до музея?",
					body: `
						<p class="faq__tx tx416">
							В Национальный музей Республики Татарстан можно добраться общественным транспортом:
						</p>
						<p class="faq__tx tx416">
							1) «Станция метро «Кремлевская», а затем по направлению к Кремлю пройдя 5 минут пешком;

						</p>`,
				},

				{
					head: "Есть ли поблизости удобная парковка?",
					body: `
						<p class="faq__tx tx416">
							В Национальный музей Республики Татарстан можно добраться общественным транспортом:
						</p>
						<p class="faq__tx tx416">
							1) «Станция метро «Кремлевская», а затем по направлению к Кремлю пройдя 5 минут пешком;

						</p>
						<p class="faq__tx tx416">
							2) Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorem harum voluptatem at aut mollitia dolore enim excepturi, quae ipsa. Ipsam, earum laboriosam tempore officiis quae natus a necessitatibus laudantium dolorum?
						</p>`,
				},

				{
					head: "Можно ли воспользоваться аудиогидом?",
					body: "Lorem ipsum dolor sit amet consectetur adipisicing elit. Ad id excepturi libero dolor, ullam beatae, voluptates inventore autem consequatur exercitationem vitae maiores incidunt iure in quo. Numquam, amet nulla? Nulla natus alias quasi aut doloremque nemo reiciendis itaque veniam nam accusantium provident quae tenetur, repudiandae sed molestiae maiores porro totam id nesciunt eos rem ut consequatur saepe? Dolorum corporis quos, sunt recusandae tenetur qui illo fuga nulla iste incidunt quidem non? Nesciunt quos accusamus distinctio ullam, earum sed, ipsam asperiores doloremque nobis vero fuga beatae aut suscipit voluptatum, necessitatibus numquam odit inventore soluta sequi. Perspiciatis, libero velit, dolore earum reprehenderit deserunt rerum dicta eius, fuga tenetur atque veniam deleniti placeat? Id aliquam laboriosam similique quibusdam iure delectus aliquid. Pariatur atque itaque laborum blanditiis animi sunt, illum fugiat aspernatur ullam quidem suscipit culpa quia natus officia numquam expedita, corrupti sequi laboriosam, molestias amet? Sapiente necessitatibus repellat ipsa fugit quod eius eos quo, expedita delectus officia minus enim impedit adipisci. Magnam tempora nesciunt deleniti quam animi quisquam iure iusto excepturi debitis tenetur, veniam voluptas aliquid molestias dignissimos aperiam. Praesentium delectus doloremque facere sint ratione saepe incidunt mollitia recusandae, consequatur debitis velit distinctio nisi in iste minima, optio quod placeat fugit inventore! Necessitatibus cumque aliquam quis accusamus similique, laborum numquam quisquam ipsam autem ab, aspernatur ipsum doloribus odio distinctio illum blanditiis repellat aut eligendi in. Voluptates hic provident tempore possimus distinctio saepe consequatur unde deleniti sunt enim atque autem expedita, perspiciatis quidem quas iure ducimus. Reprehenderit ad aliquid ratione sequi iure optio, necessitatibus ipsam veritatis maiores, odit explicabo doloremque qui, sunt beatae excepturi. Minus modi fuga, maiores amet at explicabo. Aspernatur veritatis, ratione illum nam eos adipisci repudiandae asperiores ab alias incidunt porro officia, quasi minus rem temporibus aliquid minima cum autem. Magnam beatae rem soluta eaque debitis alias id quibusdam a assumenda.",
				},
			],
		};
	},
	methods: {
		setOpenedAccordion(num) {
			const accordionsList = this.$refs.fAccordion;

			for (let index = 0; index < accordionsList.length; index++) {
				if (num !== index) {
					this.$refs.fAccordion[index].isOpen = false;
				}
			}
		},
	},
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/styles/variables.scss";

.faq {
	&__inner {
		display: flex;
		justify-content: space-between;
		gap: 30px;

		@media (max-width: $media_md) {
			display: grid;
			grid-auto-flow: row;
			gap: 20px;
		}
	}

	&__list {
		border-top: 1px solid #ffffff;
	}

	&__accordion {
		max-width: 988px;
	}
}
</style>

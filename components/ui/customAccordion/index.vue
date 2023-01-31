<template>
	<div :class="[
      'customAccordion',
      {
        open: isOpen,
      },
    ]">
		<div
			class="customAccordion__head"
			:class="{ open: isOpen }"
			@click="onToggle"
		>
			<slot name="head" />

			<div
				v-if="isCustomHeadIcon"
				class="customAccordion__iconHead"
				:class="{ 'customAccordion__iconHead_open': isOpen }"
			>
				<slot name="headIcon" />
			</div>
		</div>

		<div
			class="customAccordion__body"
			:class="{ 'customAccordion__body_open': isOpen }"
		>
			<slot name="body" />
		</div>
	</div>
</template>

<script>
export default {
  name: 'CustomAccordion',
  props: {
    isOpenProps: {
      type: Boolean,
      default: false,
    },
    isCustomHeadIcon: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      isOpen: false,
    };
  },

  created() {
    this.isOpen = this.isOpenProps;
  },

  methods: {
    onToggle() {
      this.isOpen = !this.isOpen;
      this.$emit('onToggle', this.isOpen);
    },
  },
};
</script>

<style lang="scss">
@import '~/assets/scss/styles/variables.scss';

.customAccordion {
  padding: 30px 0 30px 0;

  border-bottom-style: solid;
  border-width: 1px;
  border-color: #ffffff33;

  @media (max-width: $media_md) {
    padding: 20px 0 20px 0;
  }

  &__head {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 16px;

    cursor: pointer;
  }

  &__iconHead {
    transition: 0.3s;

    &_open {
      transform: rotate(45deg);
    }
  }

  &__body {
    max-height: 0px;

    overflow: hidden;

    opacity: 0;

    transition: opacity 0.5s ease-out, max-height 0.3s cubic-bezier(0, 1, 0, 1);

    &_open {
      padding-top: 30px;
      max-height: 5000px;

      transition: max-height 1s ease-in;

      opacity: 1;

      @media (max-width: $media_md) {
        padding-top: 20px;
      }
    }
  }
}
</style>

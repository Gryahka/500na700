<template>
	<div
		class="burgerMenu"
		:class="{
				burgerMenu_active : isVisible
    }"
	>
		<div class="burgerMenu__inner">
			<button
				class="burgerMenu__bBtn bBtn"
				:class="{
						'bBtn--active' : isVisible
				}"
				@click="$emit('setBurgerState')"
			>
				<div class="bBtn__top"></div>
				<div class="bBtn__center"></div>
				<div class="bBtn__bottom"></div>
			</button>


			<ul class="burgerMenu__list">
				<li class="burgerMenu__listItem">
					<button
						class="burgerMenu__listLink"
						@click="showSubmenu = !showSubmenu"
					>
						<div class="burgerMenu__listLink">
							Пункт 1
						</div>

						<div 
							v-if="showSubmenu"
							class="burgerMenu__wrap"
						>
							<ul class="burgerMenu__submenu submenu">
								<li 
									class="submenu__item"
									@click="$emit('setBurgerState')"
								>
									Подпункт меню
								</li>

								<li 
									class="submenu__item"
									@click="$emit('setBurgerState')"
								>
									Подпункт меню
								</li>

								<li 
									class="submenu__item"
									@click="$emit('setBurgerState')"
								>
									Подпункт меню
								</li>

								<li 
									class="submenu__item"
									@click="$emit('setBurgerState')"
								>
									Подпункт меню
								</li>
							</ul>
						</div>
					</button>
				</li>

				<li class="burgerMenu__listItem">
					<a
						class="burgerMenu__listLink"
						:class="{burgerMenu__listLink_active : activeLink === 'place2'}"
						href="#place2"
						@click="$emit('setBurgerState')"
					>
						<span class="burgerMenu__listTx tx516">
							Пункт 2
						</span>
					</a>
				</li>

				<li class="burgerMenu__listItem">
					<a
						class="burgerMenu__listLink"
						:class="{burgerMenu__listLink_active : activeLink === 'place3'}"
						href="#place3"
						@click="$emit('setBurgerState')"
					>
						<span class="burgerMenu__listTx tx516">
							Пункт 3
						</span>
					</a>
				</li>

				<li class="burgerMenu__listItem">
					<a
						class="burgerMenu__listLink"
						:class="{burgerMenu__listLink_active : activeLink === 'place4'}"
						href="#place4"
						@click="$emit('setBurgerState')"
					>
						<span class="burgerMenu__listTx tx516">
							Пункт 4
						</span>
					</a>
				</li>

				<li class="burgerMenu__listItem">
					<a
						class="burgerMenu__listLink"
						:class="{burgerMenu__listLink_active : activeLink === 'place5'}"
						href="#place5"
						@click="$emit('setBurgerState')"
					>
						<span class="burgerMenu__listTx tx516">
							Пункт 5
						</span>
					</a>
				</li>
			</ul>
		</div>

		<div 
			class="burgerMenu__overlay" 
			aria-hidden="true"
			@click="$emit('setBurgerState')"
		></div>
	</div>
</template>

<script>
export default {
  name: 'BurgerMenu',

  props: {
    isVisible: {
      type: Boolean,
      default: false,
    },
    activeLink: {
      type: String,
      default: 'place1',
    },
  },
  data() {
    return {
      showSubmenu: false,
    };
  },
  methods: {
    scrollTo(indent, elem) {
      const targetElem = document.getElementById(elem.currentTarget.hash.replace('#', ''));
      const elementPosition = targetElem.getBoundingClientRect().top;
      const offsetPosition = elementPosition + window.pageYOffset - indent;

      window.scrollTo({
        top: offsetPosition,
        behavior: 'smooth',
      });
      this.$emit('setBurgerState');
    },
  },
};
</script>

<style lang="scss" scoped>
.burgerMenu {
  position: fixed;
  z-index: 21;
  top: 0;
  right: -100%;
  bottom: 0;

  background: #0b0a0d;

  opacity: 0;
  visibility: hidden;

  transition: 0.5s;

  &_active {
    right: 0;

    opacity: 1;
    visibility: visible;
  }

  &__inner {
    display: flex;
    flex-direction: column;

    padding: 97px 0 60px;

    width: 250px;
    height: 100%;

    overflow: auto;

    box-shadow: -23px 0px 20px 0px rgb(0 0 0 / 66%);

    &::-webkit-scrollbar {
      display: none;
    }
  }

  &__bBtn {
    right: -190px;
    top: -50px;
  }

  &__list {
    display: grid;
    gap: 40px;

    margin-bottom: auto;
    padding: 0 50px 56px;
  }

  &__listItem {
  }

  &__listLink {
    display: block;

    font-family: 'MPLUS1p';
    font-weight: 500;
    font-size: 16px;
    line-height: 24px;
    color: #ffffff;
    text-align: left;
    text-decoration: none;

    &:hover {
      .burgerMenu__listTx {
        color: #75ff72;
      }
    }

    &_active {
      & .burgerMenu__listTx {
        color: var(--bd_secondary);

        &::before {
          display: block;
        }
      }
    }
  }

  &__listTx {
    transition: 0.3s;
  }

  &__submenu {
    padding: 30px 0 0 30px;
  }

  &__overlay {
    position: fixed;
    z-index: -1;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    background: rgba(0, 0, 0, 0.4);
  }
}

.bBtn {
  position: relative;

  width: 36px;
  height: 25px;

  &--active {
    .bBtn__top {
      transform: rotate(45deg) translate(8px, 8px);
    }

    .bBtn__center {
      transform: rotate(-45deg);
    }

    .bBtn__bottom {
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

.submenu {
  display: grid;
  gap: 30px;

  &__item {
    font-family: 'MPLUS1p';
    font-weight: 500;
    font-size: 14px;
    line-height: 21px;
    letter-spacing: 0.01em;

    transition: 0.3s;

    &:hover {
      color: #75ff72;
    }
  }
}
</style>

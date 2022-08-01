<template>
  <section v-click-outside="closeModal" class="modal modal--sent">
    <div class="modal__wrapper modal__wrapper-text">
      <h2 class="modal__title">Ваша заявка отправлена</h2>
      <p class="modal__text">
        Спасибо за ваше участие, ваша заявка уже поступила к нам. В ближайшее
        время мы рассмотрим ее и<br class="modal__br-mobile" />
        оповестим вас.
      </p>
    </div>
    <div
      class="modal__wrapper modal__wrapper--button modal__wrapper--mobile-only"
    >
      <button
        class="modal__button green-button"
        type="button"
        @click="closeModal"
      >
        Закрыть окно
      </button>
    </div>
  </section>
</template>

<script>
import vClickOutside from "v-click-outside";

export default {
  name: "ModalSent",
  directives: {
    clickOutside: vClickOutside.directive,
  },
  props: {
    open: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    closeModal() {
      this.$emit("close-modal-sent");
    },
  },
};
</script>

<style lang="less" scoped>
@import "./assets/styles/green-button.less";

.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: block;
  width: @mobile-width;
  text-align: center;
  margin-right: auto;
  margin-left: auto;
  background-color: @white;
  box-shadow: 0 7px 15px 0 rgba(0, 1, 1, 0.15);
  z-index: 10;

  &--sent {
    padding-top: 20px;
  }
}

.modal__wrapper {
  padding-right: 20px;
  padding-left: 20px;
  margin-right: auto;
  margin-left: auto;

  &:first-child {
    margin-bottom: 40px;
  }

  &--button {
    padding-bottom: 45px;
  }

  &--mobile-only {
    padding-top: 50px;
    background-color: @gray-dark;
  }
}

.modal__title {
  font-size: 18px;
  font-weight: 700;
  margin-top: 0;
  margin-bottom: 30px;
  color: @black;
}

.modal__text {
  margin-top: 0;
  margin-bottom: 0;
}

.modal__button {
  margin-right: auto;
  margin-left: auto;
}

@media (min-width: @tablet-width) {
  .modal {
    width: 460px;
    padding-top: 45px;
  }

  .modal__wrapper {
    padding-right: 75px;
    padding-left: 75px;
  }

  .modal__title {
    font-size: 30px;
    line-height: 40px;
    padding-right: 30px;
    padding-left: 30px;
    margin-bottom: 30px;
  }

  .modal__text {
    font-size: 18px;
  }

  .modal__br-mobile {
    display: none;
  }

  .modal__button {
    width: 300px;
  }
}

@media (min-width: @desktop-width) {
  .modal {
    width: 780px;
  }

  .modal__wrapper {
    padding-right: 195px;
    padding-left: 195px;

    &--button {
      padding-top: 50px;
      padding-right: 160px;
      padding-left: 160px;
      background-color: @gray-dark;
    }
  }

  .modal__wrapper--mobile-only .modal__button {
    width: 455px;
  }
}
</style>

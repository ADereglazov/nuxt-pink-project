<template>
  <section class="form">
    <h2 class="visually-hidden">Форма для отправки своей истории</h2>
    <p class="form__title">
      Поделитесь своей историей и получите шанс выиграть ценный приз — 1000 миль
      на вашу бонусную карту!
      <span class="form__title-hide">Пожалуйста, заполните форму ниже:</span>
    </p>
    <form id="form" class="form__form" @submit.prevent="handleSubmit">
      <div class="form__wrapper container">
        <fieldset class="form__fieldset form__fieldset--notbordered">
          <div
            v-for="item in form.person"
            :key="item.id"
            class="form__wrapper-elements form__wrapper-elements--row"
          >
            <label class="form__text-label" :for="item.id">
              {{ item.label }}
            </label>
            <input
              :id="item.id"
              :ref="item.name"
              v-model="fieldsModel[item.name]"
              :class="{
                form__required: item.required,
                'form__error-field': errors[item.name],
              }"
              :type="item.type"
              :name="item.name"
              :placeholder="item.placeholder"
              class="form__text-field"
              @input="resetFieldError(item.name)"
            />
          </div>
        </fieldset>
      </div>
      <div class="form__wrapper form__wrapper--gray">
        <div class="form__wrapper-container container">
          <fieldset class="form__fieldset form__fieldset--checkboxes">
            <legend class="form__legend form__legend--checkboxes">
              Ваши безбашенные достижения в путешествии
            </legend>
            <ul
              class="form__wrapper-elements form__wrapper-elements--checkboxes"
            >
              <li
                v-for="item in form.progress"
                :key="item.id"
                class="form__progress-checkbox"
              >
                <input
                  :id="item.id"
                  v-model="item.checked"
                  :name="item.name"
                  :checked="item.checked"
                  class="form__progress-input visually-hidden"
                  type="checkbox"
                />
                <label class="form__progress-label" :for="item.id">
                  <span class="form__progress-text">{{ item.label }}</span>
                </label>
              </li>
            </ul>
          </fieldset>
        </div>
      </div>
      <div class="form__wrapper container">
        <fieldset class="form__fieldset">
          <legend class="form__legend form__legend--hide">
            Контактная информация
          </legend>
          <div
            v-for="item in form.contacts"
            :key="item.id"
            class="form__wrapper-elements form__wrapper-elements--reverse"
          >
            <label class="form__text-label" :for="item.id">
              {{ item.label }}
            </label>
            <input
              :id="item.id"
              :ref="item.name"
              v-model="fieldsModel[item.name]"
              :class="{
                form__required: item.required,
                'form__error-field': errors[item.name],
              }"
              :type="item.type"
              :name="item.name"
              :placeholder="item.placeholder"
              :pattern="item.pattern"
              class="form__text-field"
              @input="resetFieldError(item.name)"
            />
            <svg
              class="form__icon"
              width="56"
              height="56"
              role="img"
              :aria-label="item.ariaLabel"
              focusable="false"
            >
              <use :xlink:href="iconSrc(item.iconId)"></use>
            </svg>
          </div>
        </fieldset>
      </div>
      <div class="form__wrapper form__wrapper--gray">
        <div class="form__wrapper-container container">
          <fieldset class="form__fieldset form__fieldset--radio">
            <legend class="form__legend form__legend--radiobuttons">
              С каким приложением путешествовали?
            </legend>
            <ul
              class="form__wrapper-elements form__wrapper-elements--radiobuttons"
            >
              <li
                v-for="item in form.application"
                :key="item.id"
                class="form__progress-radio"
              >
                <input
                  :id="item.id"
                  v-model="radioModel"
                  :value="item.value"
                  :checked="item.checked"
                  class="form__radio-field visually-hidden"
                  type="radio"
                  name="app"
                />
                <label class="form__radio-label" :for="item.id">
                  <span class="form__radio-text">{{ item.label }}</span>
                </label>
              </li>
            </ul>
          </fieldset>
        </div>
      </div>
      <div class="form__wrapper container">
        <fieldset class="form__fieldset">
          <legend class="form__legend">Опишите свои эмоции</legend>
          <label for="form-description" class="visually-hidden"></label>
          <textarea
            :id="form.description.id"
            v-model="form.description.value"
            :placeholder="form.description.placeholder"
            class="form__description-text"
          ></textarea>
        </fieldset>
        <div class="form__wrapper-elements form__wrapper-elements--row">
          <button
            :disabled="isFormSubmitting"
            class="form__button green-button"
            type="submit"
          >
            Отправить форму
          </button>
          <small class="form__note">
            <sup>*</sup> — обязательные
            <span class="form__note-hide">для заполнения&nbsp;</span>поля
          </small>
        </div>
      </div>
    </form>
  </section>
</template>

<script>
const SPRITE = require("~/assets/img/sprite.svg");

export default {
  name: "FormSection",
  props: {
    isFocus: {
      type: Boolean,
      default: false,
    },
  },
  data: () => ({
    form: {
      person: [
        {
          id: "surname-field",
          type: "text",
          name: "surname",
          label: "Фамилия:",
          placeholder: "Укажите фамилию *",
          required: true,
          value: "",
        },
        {
          id: "name-field",
          type: "text",
          name: "name",
          label: "Имя:",
          placeholder: "Введите ваше имя *",
          required: true,
          value: "",
        },
        {
          id: "middle-name-field",
          type: "text",
          name: "middle-name",
          label: "Отчество:",
          placeholder: "Ну и отчество тоже",
          required: false,
          value: "",
        },
      ],
      progress: [
        {
          id: "box1",
          name: "box1",
          label: "Сделал селфи с акулой",
          checked: true,
        },
        {
          id: "box2",
          name: "box2",
          label: "Обгорел на пляже",
          checked: true,
        },
        {
          id: "box3",
          name: "box3",
          label: "Видел Чака Норриса",
          checked: false,
        },
        {
          id: "box4",
          name: "box4",
          label: "Накупил сувениров",
          checked: false,
        },
        {
          id: "box5",
          name: "box5",
          label: "Удержал башню",
          checked: true,
        },
        {
          id: "box6",
          name: "box6",
          label: "Разгромил отель",
          checked: false,
        },
      ],
      contacts: [
        {
          id: "phone-field",
          type: "tel",
          name: "phone",
          label: "Номер телефона",
          placeholder: "Номер, пожалуйста",
          pattern: "\\+7\\-[0-9]{3}\\-[0-9]{3}\\-[0-9]{2}\\-[0-9]{2}",
          required: false,
          ariaLabel: "Контактный номер телефона",
          iconId: "#icon-phone",
          value: "",
        },
        {
          id: "email-field",
          type: "email",
          name: "email",
          label: "Адрес почты",
          placeholder: "Введите почту *",
          pattern: "[^@]+@[^@]+\\.[a-zA-Z]{2,6}",
          required: true,
          ariaLabel: "Контактный email",
          iconId: "#icon-mail",
          value: "",
        },
      ],
      application: [
        {
          id: "ios-field",
          value: "ios",
          label: "Pink для iOS",
          checked: true,
        },
        {
          id: "android-field",
          value: "android",
          label: "Pink на Android",
          checked: false,
        },
        {
          id: "windows-field",
          value: "windows",
          label: "Windows Phone",
          checked: false,
        },
      ],
      description: {
        id: "form-description",
        placeholder: "Можно прям в красках, не стесняясь в выражениях",
        value: "",
      },
    },
    fieldsModel: null,
    radioModel: "",
    errors: {
      surname: false,
      name: false,
      email: false,
    },
    isFormSubmitting: false,
  }),
  computed: {
    formValidatorsMap() {
      return {
        surname: this.validateSurname,
        name: this.validateName,
        email: this.validateEmail,
      };
    },
  },
  watch: {
    isFocus() {
      const errorFieldName = Object.entries(this.errors).find(
        (item) => item[1]
      );
      if (errorFieldName) {
        this.$refs[errorFieldName[0]][0].focus();
      }
    },
  },
  beforeMount() {
    this.setFieldsModelState();
    this.setRadioModelState();
  },
  methods: {
    setFieldsModelState() {
      const personFields = this.form.person.reduce((acc, current) => {
        acc[current.name] = "";
        return acc;
      }, {});

      const contactsFields = this.form.contacts.reduce((acc, current) => {
        acc[current.name] = "";
        return acc;
      }, {});

      this.fieldsModel = { ...personFields, ...contactsFields };
    },
    setRadioModelState() {
      for (let item of this.form.application) {
        if (item.checked) {
          this.radioModel = item.value;
          return;
        }
      }
    },
    iconSrc(id) {
      return SPRITE + id;
    },
    async handleSubmit() {
      let isSubmitted = false;

      if (!this.isValidForm()) {
        this.$emit(
          "form-failure",
          "Проверьте поля, выделенные красным, скорее всего вы забыли их заполнить"
        );
        return;
      }

      this.isFormSubmitting = true;
      this.setFormDataTextFieldsValues();
      this.setFormDataRadioFieldsValues();
      isSubmitted = await this.sendFormData();
      this.isFormSubmitting = false;

      if (isSubmitted) {
        this.setFieldsModelState();
        this.$emit("form-sent");
      } else {
        this.$emit(
          "form-failure",
          "Произошла ошибка при передаче данных на сервер. Попробуйте ещё раз..."
        );
      }
    },
    setFormDataTextFieldsValues() {
      for (let item of this.form.person) {
        item.value = this.fieldsModel[item.name];
      }

      for (let item of this.form.contacts) {
        item.value = this.fieldsModel[item.name];
      }
    },
    setFormDataRadioFieldsValues() {
      for (let item of this.form.application) {
        item.checked = item.value === this.radioModel;
      }
    },
    validateSurname() {
      const valid = this.fieldsModel.surname.length > 1;
      this.errors.surname = !valid;
      return valid;
    },
    validateName() {
      const valid = this.fieldsModel.name.length > 1;
      this.errors.name = !valid;
      return valid;
    },
    validateEmail() {
      const valid = this.fieldsModel.email;
      this.errors.email = !valid;
      return valid;
    },
    isValidForm() {
      const validateResults = Object.keys(this.formValidatorsMap).map(
        (field) => {
          const validator = this.formValidatorsMap[field];
          return validator();
        }
      );
      return validateResults.every(Boolean);
    },
    resetFieldError(name) {
      if (this.errors[name]) {
        this.errors[name] = false;
      }
    },
    async sendFormData() {
      const form = document.getElementById("form");
      try {
        const result = await fetch("https://echo.htmlacademy.ru", {
          method: "POST",
          body: new FormData(form),
        });
        return result.ok;
      } catch (e) {
        console.log(e);
        return false;
      }
    },
  },
};
</script>

<style lang="less" scoped>
@import "./assets/styles/green-button.less";

.form {
  background-color: @white;
}

.form__title {
  width: 280px;
  font-weight: 400;
  line-height: 30px;
  text-align: center;
  padding-top: 45px;
  padding-bottom: 20px;
  margin: 0 auto;
}

.form__title-hide {
  display: none;
}

.form__text-label,
.form__legend {
  font-weight: 400;
  line-height: 30px;
  text-transform: uppercase;
  color: @pink;
}

.form__legend {
  width: 220px;
  line-height: 18px;
  text-align: center;
  margin: 0 auto;

  &--hide {
    display: none;
  }

  &--checkboxes {
    margin-bottom: 39px;
  }

  &--radiobuttons {
    margin-bottom: 35px;
  }
}

.form__wrapper {
  padding-top: 39px;
  padding-bottom: 44px;

  &--gray {
    background-color: @gray-light;
  }

  &:first-child {
    padding-top: 15px;
  }

  &:nth-child(3) {
    padding-top: 30px;
  }

  &:last-child {
    padding-bottom: 17px;
  }
}

.form__wrapper-elements {
  display: flex;
  flex-direction: column;

  &--checkboxes,
  &--radiobuttons {
    .list-reset();
  }
}

.form__wrapper-elements--reverse + .form__wrapper-elements--reverse {
  margin-top: 20px;
}

.form__icon {
  display: none;
}

.form__fieldset {
  padding: 0;
  border: 0;
  margin: 0;
}

.form__fieldset--notbordered div + div {
  margin-top: 20px;
}

.form__progress-checkbox + .form__progress-checkbox {
  margin-top: 43px;
}

.form__progress-label {
  position: relative;
  display: flex;

  &::before {
    content: "";
    display: inline-block;
    vertical-align: middle;
    flex-shrink: 0;
    width: 39px;
    height: 39px;
    border: 2px solid @gray-lighter;
    border-radius: 2px;
    background-color: @white;
  }
}

.form__radio-text,
.form__progress-text {
  font-size: 18px;
  line-height: 30px;
  vertical-align: middle;
  padding-left: 31px;
}

.form__progress-input:not(:disabled) + .form__progress-label {
  &:hover {
    cursor: pointer;

    &::before {
      border-color: @blue-dark;
    }
  }

  &:active {
    &::before {
      border-color: @pink;
    }
  }
}

.form__progress-input:focus + .form__progress-label {
  &::before {
    border-color: @blue-dark;
  }
}

.form__progress-input:checked + .form__progress-label .form__progress-text {
  &::before {
    content: "";
    position: absolute;
    top: 22px;
    left: 8px;
    width: 10px;
    height: 2px;
    background: @pink;
    transform: rotate(45deg);
  }

  &::after {
    content: "";
    position: absolute;
    top: 18px;
    left: 12px;
    width: 22px;
    height: 2px;
    background: @pink;
    transform: rotate(-45deg);
  }
}

.form__progress-input:checked:disabled
  + .form__progress-label
  .form__progress-text {
  color: @blue-dark-opacity06;

  &::before {
    background-color: @gray-lighter;
  }

  &::after {
    background-color: @gray-lighter;
  }
}

.form__progress-input:not(:checked):disabled
  + .form__progress-label
  .form__progress-text {
  color: @blue-dark-opacity06;
}

.form__progress-radio + .form__progress-radio {
  margin-top: 38px;
}

.form__radio-label {
  display: flex;

  &::before {
    content: "";
    display: inline-block;
    vertical-align: middle;
    flex-shrink: 0;
    width: 37px;
    height: 37px;
    border: 11px solid @white;
    border-radius: 50%;
    background-color: @white;
    box-shadow: 0 0 0 2px @gray-lighter;
  }
}

.form__radio-field:checked:not(:disabled) + .form__radio-label {
  &::before {
    background-color: @pink;
  }
}

.form__radio-field:not(:disabled) + .form__radio-label {
  &:hover {
    cursor: pointer;

    &::before {
      box-shadow: 0 0 0 2px @black;
    }
  }

  &:active {
    &::before {
      box-shadow: 0 0 0 2px @pink;
    }
  }
}

.form__radio-field:checked:disabled + .form__radio-label::before {
  background-color: @gray-lighter;
}

.form__radio-field:checked:disabled + .form__radio-label .form__radio-text {
  color: @blue-dark-opacity06;
}

.form__radio-field:not(:checked):disabled
  + .form__radio-label
  .form__radio-text {
  color: @blue-dark-opacity06;
}

.form__radio-field:focus + .form__radio-label {
  &::before {
    box-shadow: 0 0 0 2px @black;
  }
}

.form__text-label {
  padding-left: 23px;
  margin-bottom: 5px;
}

.form__text-field {
  height: 56px;
  padding: 0 20px;
  background-color: @white;
  border: none;
  border-radius: 2px;
  box-shadow: 0 0 0 40px inset white, 0 0 0 2px @gray-lighter;

  &:hover {
    box-shadow: 0 0 0 2px @black;
  }

  &:focus {
    outline: none;
    box-shadow: 0 0 0 2px @pink;
  }

  &:-webkit-autofill,
  &:-webkit-autofill:hover,
  &:-webkit-autofill:focus,
  &:-webkit-autofill:active {
    -webkit-background-clip: text;
    transition: background-color 5000s ease-in-out 0s;
  }

  /* Убираем "крестики" в инпутах для IE */
  &[type="text"]::-ms-clear,
  &[type="text"]::-ms-reveal {
    display: none;
    width: 0;
    height: 0;
  }
}

.form__required.form__error-field {
  box-shadow: 0 0 0 2px @pink;
}

.form__text-field::placeholder,
.form__description-text::placeholder {
  font-size: 18px;
  line-height: 30px;
  color: @blue-dark;
}

.form__note {
  max-width: 315px;
  font-size: 14px;
  font-weight: 400;
  text-align: center;
  text-transform: uppercase;
  margin-top: 40px;

  sup {
    top: 0;
    font-size: 14px;
    color: @pink;
  }
}

.form__note-hide {
  display: none;
}

.form__description-text {
  resize: none;
  width: 100%;
  height: 200px;
  font-size: 18px;
  line-height: 30px;
  padding: 15px 20px;
  margin-top: 14px;
  margin-bottom: 42px;
  border: 2px solid @gray-lighter;
  border-radius: 2px;

  &:hover {
    border-color: @black;
  }

  &:active {
    border-color: @pink;
  }

  &:focus {
    outline: none;
    border-color: @pink;
  }
}

@media (min-width: @tablet-width) {
  .form__title {
    width: 490px;
    font-size: 18px;
    padding-top: 91px;
    margin-bottom: 53px;
  }

  .form__title-hide {
    display: inline-block;
  }

  .form__form {
    display: flex;
    flex-direction: column;
  }

  .form__fieldset {
    padding-right: 60px;
    padding-left: 58px;
    border: 2px solid @gray-light;

    &--notbordered {
      padding-right: 0;
      padding-left: 0;
      border: 0;
    }

    &--notbordered div + div {
      margin-top: 55px;
    }

    &--radio {
      padding-top: 44px;
      padding-bottom: 55px;
    }
  }

  .form__legend {
    width: inherit;
    padding: 0 30px;
    margin: 0;

    &--hide {
      display: table;
      margin-bottom: 38px;
    }

    &--checkboxes {
      margin-bottom: 43px;
    }
  }

  .form__wrapper {
    padding-top: 0;
    padding-bottom: 0;

    &--gray {
      background-color: @white;
    }

    &:first-child {
      padding-top: 0;
      padding-bottom: 0;
    }

    &:nth-child(2) {
      order: 4;
    }

    &:nth-child(3) {
      padding-top: 0;
      order: 3;
    }

    &:nth-child(4) {
      order: 2;
    }

    &:nth-child(5) {
      order: 5;
    }

    &:last-child {
      padding-bottom: 50px;
    }
  }

  .form__wrapper + .form__wrapper {
    margin-top: 58px;
  }

  .form__wrapper-elements {
    &--row {
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
    }

    &--reverse {
      position: relative;
      flex-direction: column-reverse;
      margin-bottom: 30px;
    }

    &--reverse:last-child {
      margin-bottom: 25px;
    }
  }

  .form__wrapper-elements--row label {
    padding-right: 19px;
    padding-left: 0;
  }

  .form__wrapper-elements--row input {
    flex-grow: 1;
  }

  .form__wrapper-elements--reverse input {
    padding-right: 80px;
    padding-left: 17px;
    margin-bottom: 12px;
  }

  .form__wrapper-elements--reverse + .form__wrapper-elements--reverse {
    margin-top: 0;
  }

  .form__icon {
    position: absolute;
    top: 0;
    right: 0;
    display: block;
    width: 56px;
    height: 56px;
    border: 20px solid @gray-lighter;
    background-color: @gray-lighter;
    pointer-events: none;
  }

  .form__radio-text {
    padding-left: 22px;
  }

  .form__progress-checkbox {
    &:last-child {
      margin-bottom: 47px;
    }
  }

  .form__progress-text {
    padding-left: 20px;
  }

  .form__text-label {
    padding-left: 18px;
    margin-bottom: 0;
  }

  .form__description-text {
    width: 498px;
    height: 195px;
    padding: 15px 18px;
    margin-top: 38px;
    margin-bottom: 42px;
  }

  .form__wrapper-elements .form__button {
    width: 300px;
  }

  .form__button,
  .form__note {
    margin-top: 68px;
  }
}

@media (min-width: @desktop-width) {
  .form__title {
    width: 775px;
    min-height: 200px;
    margin-bottom: 38px;
  }

  .form__form {
    flex-direction: row;
    flex-wrap: wrap;
    width: @desktop-width;
    margin: 0 auto;
  }

  .form__fieldset {
    padding-right: 58px;

    &--notbordered {
      width: 435px;
    }

    &--radio {
      min-height: 305px;
      padding: 45px 20px;
    }

    &--checkboxes {
      padding-right: 0;
      min-height: 242px;
    }
  }

  .form__wrapper {
    &:first-child {
      width: 455px;
      margin-left: 0;
    }

    &:nth-child(4) {
      margin-top: -15px;
    }

    &:last-child {
      padding-bottom: 0;
    }
  }

  .form__wrapper:nth-child(4) .form__wrapper-container {
    width: 445px;
    padding-left: 0;
  }

  .form__wrapper-elements {
    &--reverse {
      float: left;
      width: 372px;
      margin-bottom: 12px;
    }

    &--reverse:last-child {
      margin-bottom: 12px;
    }

    &--checkboxes {
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: space-between;
      align-content: flex-start;
    }
  }

  .form__wrapper-elements--reverse:nth-child(odd) {
    margin-left: 73px;
  }

  .form__wrapper-elements--reverse input {
    padding-right: 80px;
  }

  .form__legend {
    &--radibuttons {
      margin-bottom: 18px;
    }

    &--hide {
      margin-bottom: 36px;
    }
  }

  .form__radio-label {
    padding-left: 55px;
  }

  .form__progress-checkbox + .form__progress-checkbox {
    margin-top: 0;
  }

  .form__progress-checkbox {
    width: 267px;
    margin-bottom: 43px;

    &:nth-of-type(2) {
      order: 4;
    }

    &:nth-of-type(3) {
      margin-right: auto;
      margin-left: 47px;
    }

    &:nth-of-type(4) {
      order: 5;
      margin-right: auto;
      margin-left: 47px;
    }

    &:last-child {
      order: 6;
      margin-bottom: 43px;
    }
  }

  .form__radio-text {
    padding-left: 20px;
  }

  .form__description-text {
    width: 820px;
    height: 125px;
    padding: 12px 17px;
    margin-top: 32px;
    margin-bottom: 38px;
  }

  .form__button,
  .form__note {
    margin-top: 65px;
  }

  .form__note-hide {
    display: inline-block;
  }
}
</style>

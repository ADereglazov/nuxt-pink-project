<template>
  <section class="contacts">
    <h2 class="visually-hidden">Наши контакты</h2>
    <div class="contacts__wrapper container">
      <p class="contacts__title">Остались вопросы? Свяжитесь с нами!</p>
      <div class="contacts__info">
        <div class="contacts__call-info">
          <b class="contacts__info-title">Звоните:</b>
          <a class="contacts__info-detail" href="tel:+78125556666"
            >+7 (812) 555-66-66</a
          >
        </div>
        <div class="contacts__write-info">
          <b class="contacts__info-title">Пишите:</b>
          <a
            class="contacts__info-detail contacts__info-detail--email"
            href="mailto:mail@htmlacademy.ru"
            >mail@htmlacademy.ru</a
          >
        </div>
        <div class="contacts__welcome-info">
          <b class="contacts__info-title">Приезжайте в гости:</b>
          <address class="contacts__info-detail">
            ул. Большая Конюшенная, 19/8
          </address>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactsSection",
};
</script>

<style lang="less" scoped>
.contacts {
  text-align: center;
  background-color: @white;
}

.contacts__wrapper {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  min-height: 380px;
  padding-top: 42px;
}

.contacts__title {
  font-size: 24px;
  font-weight: 300;
  line-height: 30px;
  margin: 0 auto;
}

.contacts__info-title {
  font-size: 18px;
  font-weight: 700;
  line-height: 30px;
}

.contacts__info {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 245px;
  margin-top: 30px;
}

.contacts__info-detail {
  display: inline-block;
  vertical-align: middle;
  font-size: 24px;
  font-weight: 300;
  font-style: normal;
  line-height: 30px;
  text-decoration: none;
  color: @pink;

  &--email:hover {
    text-decoration: underline;
    color: @blue-dark;
  }

  &--email:active {
    text-decoration: none;
    color: @blue-dark-opacity03;
  }
}

@media (min-width: @tablet-width) {
  .contacts__wrapper {
    min-height: 400px;
    padding-top: 45px;
  }

  .contacts__title {
    font-size: 40px;
    line-height: 50px;
    width: 370px;
    margin: 0 auto;
  }

  .contacts__info {
    flex-direction: row;
    flex-wrap: wrap;
    align-content: space-between;
    min-height: 195px;
    margin: 40px 28px 0 26px;
  }

  .contacts__info div {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    width: 245px;
  }

  .contacts__info-title {
    margin-bottom: 0;
  }

  .contacts__welcome-info {
    margin: 0 auto;
  }
}

@media (min-width: @desktop-width) {
  .contacts__wrapper {
    justify-content: space-between;
    min-height: 370px;
    padding-top: 67px;
    padding-bottom: 20px;
  }

  .contacts__title {
    font-size: 50px;
    line-height: 60px;
    width: 465px;
  }

  .contacts__info {
    min-height: 100px;
    margin: 53px 27px 0 28px;
  }

  .contacts__info div {
    min-height: 100px;
  }

  .contacts__info-title {
    margin-bottom: 20px;
  }

  .contacts__write-info {
    order: 2;
  }

  .contacts__welcome-info {
    margin: 0;
    order: 1;
  }
}
</style>

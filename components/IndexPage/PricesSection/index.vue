<template>
  <section class="prices">
    <h2 class="visually-hidden">Цены на приложение Pink</h2>
    <div class="prices__wrapper slider container">
      <table
        :style="{ alignItems: tablePositions[tablePosition] }"
        class="prices__table slider__list"
      >
        <tbody>
          <tr class="prices__row">
            <th
              v-for="column in tablePrices.tableHead"
              :key="column.name"
              :class="{ 'prices__head--hit': column.hit }"
              class="prices__head"
            >
              <template v-if="column.name">
                <b class="prices__name">{{ column.name }}</b>
                <span class="prices__price">{{ column.price }}</span>
              </template>
              <template v-if="column.hit">
                <svg class="prices__img-hit" width="74" height="73">
                  <use xlink:href="~/assets/img/sprite.svg#icon-hit"></use>
                </svg>
                <svg
                  class="prices__img-hit-tablet"
                  width="61"
                  height="61"
                  role="img"
                  aria-label="Хит продаж"
                  focusable="false"
                >
                  <use
                    xlink:href="~/assets/img/sprite.svg#icon-hit-tablet"
                  ></use>
                </svg>
                <span class="prices__hit">ХИТ</span>
              </template>
            </th>
          </tr>
          <tr
            v-for="row in tablePrices.tableData"
            :key="row.name"
            class="prices__row"
          >
            <td
              v-for="(column, index) in row.data"
              :key="column + index"
              :class="{
                'prices__data--yes': column && index !== 0,
                'prices__data--no': !column && index !== 0,
              }"
              class="prices__data"
            >
              <template v-if="index === 0">
                {{ row.name }}
              </template>
              <span v-else class="prices__text-mobile">
                {{ row.name }}
              </span>
            </td>
          </tr>
        </tbody>
      </table>
      <ul class="prices__toggles slider__toggles">
        <li
          v-for="(item, index) in tablePositions"
          :key="index"
          class="slider__item"
        >
          <button
            :class="{ 'slider__toggle--current': tablePosition === index }"
            class="slider__toggle"
            type="button"
            @click="tablePosition = index"
          ></button>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "PricesSection",
  data: () => ({
    tablePrices: {
      tableHead: [
        { name: "", price: "", hit: false },
        { name: "База", price: "1,99 USD", hit: false },
        { name: "Стандарт", price: "3,99 USD", hit: true },
        { name: "Анлим", price: "9,99 USD", hit: false },
      ],
      tableData: [
        {
          name: "Розовый фильтр",
          data: [false, true, true, true],
        },
        {
          name: "Смайлики",
          data: [false, false, true, true],
        },
        {
          name: "Комментарии",
          data: [false, false, false, true],
        },
      ],
    },
    tablePositions: ["flex-start", "center", "flex-end"],
    tablePosition: 1,
  }),
};
</script>

<style lang="less" scoped>
@import "./assets/styles/slider.less";

.prices {
  overflow: hidden;
  min-height: 470px;
  background-image: url("~assets/img/bg-triangle-white.svg");
  background-repeat: no-repeat;
  background-position: top center;
  background-size: contain;
}

.prices__table {
  display: flex;
  flex-direction: column;
  align-items: center;
  table-layout: fixed;
  line-height: 30px;
  margin-top: 89px;
  margin-bottom: 40px;
  border-collapse: collapse;
}

.prices__head {
  min-width: 275px;
  text-align: center;
  border: 2px solid @gray-light;
  color: @white;
  background-color: @blue-dark;

  &--hit {
    position: relative;
  }
}

.prices__head:first-child,
.prices__data:first-child {
  display: none;
}

.prices__name {
  display: block;
  font-size: 18px;
  font-weight: 700;
  text-align: center;
  text-transform: uppercase;
}

.prices__price {
  display: block;
  font-size: 24px;
  font-weight: 300;
  text-align: center;
  padding-bottom: 4px;
}

.prices__img-hit {
  display: block;
  position: absolute;
  top: 0;
  left: -2px;
}

.prices__img-hit-tablet {
  display: none;
}

.prices__hit {
  display: block;
  position: absolute;
  top: 12px;
  left: 8px;
  transform: rotate(-45deg);
  font-size: 14px;
  font-weight: 400;
}

.prices__row {
  font-weight: 400;
  height: 60px;
  vertical-align: middle;
  background-color: @white;
}

.prices__row:first-child {
  height: 100px;
}

.prices__data {
  position: relative;
  text-align: left;
  padding-left: 20px;
  border: 2px solid @gray-lighter;

  &--yes {
    &::before {
      content: "";
      position: absolute;
      top: 33px;
      right: 30px;
      width: 14px;
      height: 3px;
      border-radius: 2px;
      background: @green;
      transform: rotate(45deg);
    }

    &::after {
      content: "";
      position: absolute;
      top: 28px;
      right: 9px;
      width: 29px;
      height: 3px;
      border-radius: 2px;
      background: @green;
      transform: rotate(-45deg);
    }
  }

  &--no {
    &::before {
      content: "";
      position: absolute;
      top: 28px;
      right: 11px;
      width: 36px;
      height: 3px;
      border-radius: 2px;
      background: @orange;
      transform: rotate(45deg);
    }

    &::after {
      content: "";
      position: absolute;
      top: 28px;
      right: 11px;
      width: 36px;
      height: 3px;
      border-radius: 2px;
      background: @orange;
      transform: rotate(-45deg);
    }
  }
}

.prices__text-mobile {
  text-transform: uppercase;
}

@media (min-width: @tablet-width) {
  .prices {
    min-height: 380px;
  }

  .prices__wrapper {
    padding-top: 92px;
    padding-bottom: 20px;
  }

  .prices__table {
    display: table;
    width: 100%;
    margin: 0;
  }

  .prices__head:first-child,
  .prices__data:first-child {
    display: table-cell;
  }

  .prices__head:first-child {
    border: none;
    background-color: @gray-light;
  }

  .prices__data--yes {
    &::before {
      top: 25px;
      right: 79px;
    }

    &::after {
      top: 19px;
      right: 57px;
    }
  }

  .prices__data--no {
    &::before {
      top: 19px;
      right: 59px;
    }

    &::after {
      top: 19px;
      right: 59px;
    }
  }

  @media (max-width: @mobile-width-only) {
    .prices__head {
      padding-top: 8px;
    }

    .prices__price {
      font-size: 18px;
    }

    .prices__name {
      font-size: 16px;
      line-height: 24px;
    }

    .prices__img-hit {
      display: none;
    }

    .prices__img-hit-tablet {
      display: block;
      position: absolute;
      top: 0;
      left: 0;
    }

    .prices__row {
      height: 47px;
    }

    .prices__row:first-child {
      height: 79px;
    }

    .prices__data {
      padding-left: 15px;
    }
  }

  .prices__hit {
    top: 2px;
    left: 7px;
  }

  .prices__data {
    &--yes,
    &--no {
      background-position: 50%;
    }
  }

  .prices__text-mobile,
  .prices__toggles {
    display: none;
  }
}

@media (min-width: @desktop-width) {
  .prices {
    min-height: 515px;
  }

  .prices__wrapper {
    padding-top: 142px;
  }

  .prices__row {
    font-size: 18px;
  }

  .prices__img-hit {
    left: 0;
  }

  .prices__hit {
    top: 11px;
    left: 11px;
  }

  .prices__data--yes {
    &::before {
      top: 33px;
      right: 119px;
    }

    &::after {
      top: 29px;
      right: 97px;
    }
  }

  .prices__data--no {
    &::before {
      top: 28px;
      right: 98px;
    }

    &::after {
      top: 28px;
      right: 98px;
    }
  }
}
</style>

<template>
  <div class="overlay-wrapper">
    <button
      class="toggle-btn"
      @click="
        toggleEvent();
        getRandomNum();
      "
    >
      {{ showEvent ? 'Hide' : 'Show' }} Event
    </button>
    <div class="overlay-card" v-if="showEvent && events && events.length">
      <div class="inner-card">
        <div
          class="card-row"
          :style="{ 'background-color': chosenEvent.color }"
        >
          <h1>
            {{ chosenEvent.name }}
          </h1>
        </div>
        <div class="card-row">
          <h3>
            {{ chosenEvent.from }} -
            {{ chosenEvent.to }}
          </h3>
        </div>
        <div
          class="card-row"
          :style="{ 'background-color': chosenEvent.color }"
        >
          <div class="talents-wrapper">
            <div
              class="talents-box"
              v-for="talent in chosenEvent.talent"
              :key="talent"
            >
              <h5>
                {{ talent }}
              </h5>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import eventsData from '../assets/eventsData.json';

export default {
  name: 'OverLay',
  data() {
    return {
      events: eventsData,
      showEvent: false,
      chosenEvent: '',
    };
  },
  methods: {
    toggleEvent() {
      this.showEvent = !this.showEvent;
    },
    getRandomNum() {
      var chosenNumber = Math.floor(Math.random() * this.events.length);
      this.chosenEvent = this.events[chosenNumber];
    },
  },
};
</script>

<style scoped lang="scss">
.overlay-wrapper {
  width: 120rem;
  height: 59.375rem;
  display: flex;
  justify-content: center;
  align-items: center;

  .toggle-btn {
    padding: 10px 20px;
    color: $default-black;
    background-color: $default-white;
    cursor: pointer;
    border-radius: $default-radius;
    min-width: 8rem;
  }
}
.overlay-card {
  padding: 4px;
  text-align: center;
  width: 60rem;
  background-color: $default-white;
  border-radius: $default-radius;

  .inner-card {
    border: $border-thick solid $default-black;
    border-radius: $default-radius;
    display: grid;
    grid-template-rows: 2fr 1.5fr 2fr;

    .card-row {
      display: flex;
      align-items: center;
      justify-content: center;
      &:nth-child(1) {
        border-top-left-radius: $inner-radius;
        border-top-right-radius: $inner-radius;
      }
      &:nth-child(2) {
        border-top: $border-thick solid $default-black;
        border-bottom: $border-thick solid $default-black;
      }
      &:nth-child(3) {
        border-bottom-left-radius: $inner-radius;
        border-bottom-right-radius: $inner-radius;
      }

      h1,
      h5 {
        font-size: 36px;
        color: $default-white;
        text-shadow: 3px 3px 2px $default-black;
      }

      h1 {
        text-transform: uppercase;
      }

      h3 {
        font-size: 24px;
        font-weight: 400;
      }

      .talents-wrapper {
        display: flex;
        height: 100%;
        width: 100%;

        .talents-box {
          flex: 1;
          display: flex;
          align-items: center;
          justify-content: center;

          &:not(:first-child) {
            border-left: $box-border-thick solid black;
          }
          &:not(:last-child) {
            border-right: $box-border-thick solid black;
          }
        }
      }
    }
  }
}
</style>

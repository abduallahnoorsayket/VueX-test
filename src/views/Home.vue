<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <div class="counter" :style="{color: $store.state.colorCode }">{{ $store.state.counter }}</div>
    <div class="counter-sqared">
      {{$store.state.counter}}
      <sup>2</sup>
      =
      {{ $store.getters.counterSquared}}
    </div>
    <div class="buttons">
      <button @click="$store.dispatch('decreaseCounter')">-</button>
      <button @click="$store.dispatch('increaseCounter')">+</button>
    </div>
    <input v-model="colorCode" type="text" placeholder="Enter color" />
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  computed: {
    colorCode: {
      get() {
        return this.$store.state.colorCode;
      },
      set(newValue) {
        this.$store.dispatch("setColorCode", newValue);
      },
    },
  },
};
</script>

<style scoped>
.div {
  margin-bottom: 10px;
}
.counter {
  font-size: 80px;
}
.buttons button {
  font-size: 40px;
  width: 100px;
  margin: 15px 10px;
}
</style>
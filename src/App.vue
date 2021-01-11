<template>
  <div id="app">
    <section class="test">
      <h1 class="test__heading">Create a Spiral</h1>
      <p class="test__description">
        Choose the size of the spiral
      </p>
      <label for="spiral" style="display: block;">Spiral Size</label>
      <input
        id="spiral"
        name="spiral"
        v-model="spiralSize"
        type="number"
        class="test__input"
        min="0"
        max="100"
      />
      <button class="test__button-create" on:click="createSpiral">
        Create
      </button>
    </section>
    <section class="spiral">
      <div v-for="n in spiralSize" :key="n">
        <MyBlock :id="n" />
      </div>
    </section>
  </div>
</template>

<script>
import MyBlock from "./components/MyBlock";
export default {
  name: "App",
  components: {
    MyBlock,
  },
  data() {
    return {
      spiralSize: 0,
    };
  },
  methods: {
    createSpiral() {},
  },
};
</script>

<style>
.test {
  padding: 3rem;
  font-size: 2rem;
  text-align: center;
  background-color: #eee;
  box-shadow: 0 1rem 2rem rgba(0, 0, 0, 0.4);
}
.text__description {
  text-align: left;
}
.test__button-create {
  display: block;
  margin: 2rem 50%;
  transform: translateX(-50%);
  background-color: #1a508b;
  color: #fff3e6;
  border: none;
  cursor: pointer;
  border-radius: 10rem;
  padding: 1rem;
  font-size: 1rem;
  outline-style: none;
  transition: 0.2s all;
  text-transform: uppercase;
}
.test__button-create:hover {
  transform: translate(-50%, -0.2rem);
  box-shadow: 0 0.4rem 1rem rgba(0, 0, 0, 0.4);
}
.test__button-create:active {
  transform: translate(-50%, -0.1rem);
  box-shadow: 0 0.2rem 1rem rgba(0, 0, 0, 0.4);
}

.spiral {
  text-align: center;
  margin: 3rem;
}
</style>

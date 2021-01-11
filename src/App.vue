/* eslint-disable */
<template>
  <div id="app">
    <section class="test">
      <h1 class="test__heading">Create a Spiral</h1>
      <p class="test__description">
        Choose the initial size of the spiral
      </p>
      <p>Total number of blocks {{ spiralTotalSize }}</p>
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

      <button @click="createMatrix">create</button>
    </section>
    <section class="spiral">
      <MyBlock v-for="n in matrix.length" :key="n" :style="blockPosition(n)">
      </MyBlock>
      {{ matrix }}
    </section>
  </div>
</template>

<script>
import MyBlock from "./components/MyBlock";
import Vue from "vue";
export default {
  name: "App",
  components: {
    MyBlock,
  },
  data() {
    return {
      spiralSize: 10,
      matrix: [],
    };
  },
  methods: {
    createMatrix() {
      var turn = 0;
      var spiralSize = this.spiralSize;
      var x = 0;
      var y = 0;
      var matrix = [];
      for (let index = 0; index <= spiralSize; index++) {
        if (index == spiralSize - 1) {
          index = 0;
          spiralSize--;
          if (turn < 4) {
            turn++;
          } else {
            turn = 0;
          }
        }
        if (turn == 0) {
          matrix.push({ posx: x, posy: y });
          x++;
        } else if (turn == 1) {
          matrix.push({ posx: x, posy: y });
          y++;
        } else if (turn == 2) {
          matrix.push({ posx: x, posy: y });
          x--;
        } else if (turn == 3) {
          matrix.push({ posx: x, posy: y });
          y--;
        }
      }
      this.matrix = matrix;
      console.log("1");
      this.$nextTick(() => {});
    },
    blockPosition(n) {
      console.log("2");
      Vue.nextTick(() => {
        return {
          left: `${this.matrix[n].posx * 40}px`,
          top: `${this.matrix[n].posy * 40}px`,
        };
      });
    },
  },

  computed: {
    spiralTotalSize() {
      var total = 1;
      for (let index = this.spiralSize - 1; index >= 0; index--) {
        total += index;
      }
      return total;
    },
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
  position: relative;
}
</style>

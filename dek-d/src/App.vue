<script setup>
import { ref, reactive, onBeforeMount } from "vue";

const slides = reactive([
  { src: "https://picsum.photos/id/241/500/300" },
  { src: "https://picsum.photos/id/230/500/300" },
  { src: "https://picsum.photos/id/277/500/300" },
  { src: "https://picsum.photos/id/251/500/300" },
  { src: "https://picsum.photos/id/233/500/300" },
]);

let curIndex = ref(2);

const gotoPrev = () => {
  curIndex.value > 0 ? curIndex.value-- : "";
};

const gotoNext = () => {
  curIndex.value < 4 ? curIndex.value++ : "";
};

const checkSlide = (index) => {
  curIndex.value = index;
};

</script>

<template>
  <div class="page">
    <div class="slide" >
      <button class="button button-left" type="button" @click="gotoPrev()">
        <i class="arrow left"></i>
      </button>
      <div>
        <img :src="slides[curIndex].src" />
      </div>
      <button class="button  button-right" type="button" @click="gotoNext()">
        <i class="arrow right"></i>
      </button>
    </div>
    <div>
      <span v-for="(slide, index) in slides" :key="index">
        <input
          class=""
          type="radio"
          id="color"
          name="slide"
          v-on:click="checkSlide(index)"
          :checked="index == curIndex"
        />
      </span>
    </div>
  </div>
</template>

<style>
.page {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
}

.slide {
  display: flex;
  flex-direction: row;
}

.arrow {
  border: solid black;
  border-width: 0 3px 3px 0;
  display: inline-block;
  padding: 3px;  
}

.right {
  transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
}

.left {
  transform: rotate(135deg);
  -webkit-transform: rotate(135deg);  
}

.button {
  background-color: transparent;
  border-color: transparent;
}
.button:hover {
	background-color: rgb(255, 255, 255,0.4);
}
.button:active {
  position:relative;
	top:1px;
}

.button-left {
  position: relative;
  transform: translate(23px, 0px);
  z-index: 1;
}
.button-right {
  position: relative;
  transform: translate(-25px, 0px);
  z-index: 1;
}

input[type=radio]#color {
            accent-color: rgb(212, 122, 26);
        }

</style>

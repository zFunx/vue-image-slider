<template>
  <div class="container" v-if="imgs">
    <div class="prev-btn" @click="prevImg">&lt;</div>
    <Transition
      :enter-from-class="
        isReversedAnim ? 'reverse-enter-from' : 'forward-enter-from'
      "
      :leave-to-class="isReversedAnim ? 'reverse-leave-to' : 'forward-leave-to'"
    >
      <IMG :src="imgs[currentImgIndex]" v-if="showFirstImg" />
      <IMG :src="imgs[currentImgIndex]" v-else />
    </Transition>
    <div class="next-btn" @click="nextImg">&gt;</div>
  </div>
</template>
<script setup>
import { ref, defineProps } from "vue";
import IMG from "./IMG";

const props = defineProps({
  imgs: Array,
});

const currentImgIndex = ref(0);
const showFirstImg = ref(true);
const isReversedAnim = ref(false); // is animation reversed?

function prevImg() {
  isReversedAnim.value = true;
  if (currentImgIndex.value == 0) {
    currentImgIndex.value = props.imgs.length - 1;
  } else {
    currentImgIndex.value = --currentImgIndex.value;
  }
  showFirstImg.value = !showFirstImg.value;
}

function nextImg() {
  isReversedAnim.value = false;
  currentImgIndex.value = ++currentImgIndex.value % props.imgs.length;
  showFirstImg.value = !showFirstImg.value;
}
</script>
<style scoped>
.container {
  position: relative;
  height: 300px;
  width: 300px;
  overflow: hidden;
}

.container > .prev-btn,
.container > .next-btn {
  background: white;
  height: 50px;
  width: 50px;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  z-index: 1;
  display: flex;
  align-items: center;
  font-weight: bolder;
  cursor: pointer;
  opacity: 0;
  transition: 0.3s;
}

.container > .prev-btn {
  border-radius: 0 8px 8px 0;
  padding-right: 12px;
  justify-content: end;
  transform: translate(-50%, -50%);
}

.container > .next-btn {
  border-radius: 8px 0 0 8px;
  right: 0;
  padding-left: 12px;
  justify-content: start;
  transform: translate(50%, -50%);
}

.container:hover > .prev-btn,
.container:hover > .next-btn {
  opacity: 0.8;
}

.v-enter-active,
.v-leave-active {
  transition: all 0.3s ease-out;
}

.forward-enter-from {
  transform: translateX(-100%);
}

.forward-leave-to {
  transform: translateX(100%);
}

.reverse-enter-from {
  transform: translateX(100%);
}

.reverse-leave-to {
  transform: translateX(-100%);
}
</style>
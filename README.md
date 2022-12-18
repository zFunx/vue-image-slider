# vue-image-slider
Image Slider using `<Transition>` component

I was learning how to animate in Vue here https://vuejs.org/guide/built-ins/transition.html#css-based-transitions and thinking why install another carousel or slider package when we can make a slider using `<Transition>` component? Everything is around us. Just need to look

```html
<template>
  <ImageSlider :imgs="images" />
</template>

<script setup>
    import ImageSlider from "./ImageSlider";

    // Images
    import img1 from "./assets/beautiful-rain.jpg";
    import img2 from "./assets/tree.jpg";
    import img3 from "./assets/water.jpg";
    const images = [img1, img2, img3];
</script>
```
![Showcase](handmade.gif "Showcase")

Feel free to correct me✌
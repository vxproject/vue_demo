<template>
  <div>
    <img src="./assets/mazei.jpg" class="img">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  }
};
</script>

<style>
.img {
  height: 100px;
  width: 100px;
  border-radius: 100px;
  margin: 100px;
}
</style>

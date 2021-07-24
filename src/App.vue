<template>
  <div >
    <Header />
    <summodel />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import summodel from "./components/summodel.vue";
import Header from "./components/header.vue";

@Component({
  components: {
    summodel,
    Header
  }
})
export default class App extends Vue {}
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  font-family: 'Varela Round', sans-serif;
}
</style>

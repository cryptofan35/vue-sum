<template>
  <div class="header">CALCULATOR</div>
</template>

<script lang="ts">
import { Vue } from "vue-property-decorator";

export default class Header extends Vue {}
</script>

<style>
.header {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  background-color: #cc0631 !important;
  width: 100%;
  height: 70px;
  line-height: 70px;
  text-align: center;
}
</style>

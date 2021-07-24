<template>
  <div class="hello-wrapper">
    <p class="number-title">Enter the numbers</p>
    <div class="input-wrapper">
      <input placeholder="number 1" id="name" v-model="num1" type="number" />
      <input placeholder="number 2" id="name2" v-model="num2" type="number" />
    </div>
    <div class="sum-btn">
      <button v-on:click="reverseMessage">Sum</button>
    </div>
    <div class="border-set"></div>
    <div class="Results">
      <p class="Results-title">Results</p>
      <p class="Results-set">{{this.sum}}</p>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import vueAxios from "v-axios";
import axios from "axios";
import VueToast from "vue-toast-notification";
import "vue-toast-notification/dist/theme-sugar.css";
Vue.use(vueAxios, axios);
Vue.use(VueToast);

export default Vue.extend({
  name: "Home",
  props: {
    data: String
  },
  data() {
    return {
      num1: "",
      num2: "",
      sum: ""
    };
  },
  methods: {
    reverseMessage() {
      if (this.num1 && this.num2) {
        axios
          .post("https://sum-vue.herokuapp.com/sum", {
            Num1: parseFloat(this.num1),
            Num2: parseFloat(this.num2)
          })
          .then(response => (this.sum = response.data.sum));
      } else {
        Vue.$toast.error("Please Enter Number");
      }
    }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello-wrapper {
  width: 740px;
  margin: auto;
  background: #ffffff 0% 0% no-repeat padding-box;
  box-shadow: 2px 6px 10px #00000029;
  border: 0.5px solid #a4a4a4;
  border-radius: 4px;
  padding: 20px 30px;
  text-align: center;
  margin-top: 50px;
  box-sizing: border-box;
}
.hello-wrapper .number-title {
  font-size: 16px;
  letter-spacing: 0px;
  color: #a4a4a4;
  margin-bottom: 15px;
}
.hello-wrapper .input-wrapper input {
  padding: 9px 10px;
  background: #ffffff;
  border: 1px solid #a4a4a4;
  border-radius: 2px;
  width: 100%;
  max-width: 227px;
  display: block;
  margin: 12px auto;
  color: #a4a4a4;
}
.hello-wrapper .sum-btn button {
  background: #c10708;
  border-radius: 2px;
  max-width: 248px;
  display: block;
  margin: 12px auto;
  width: 100%;
  padding: 9px 10px;
  border: 1px solid #fff;
  color: #ffffff;
  letter-spacing: 0.16px;
  border-radius: 2px;
}
.hello-wrapper .border-set {
  border: 1px solid #c10708;
  margin: 40px 0px;
}
.hello-wrapper .Results p.Results-title {
  color: #a4a4a4;
  font-size: 16px;
  padding: 0px 0px 15px 0px;
}
.hello-wrapper .Results p.Results-set {
  font-size: 16px;
  background: #ffffff 0% 0% no-repeat padding-box;
  border: 1px solid #c10708;
  border-radius: 2px;
  width: 100%;
  max-width: 227px;
  margin: auto;
  text-align: left;
  padding: 8px 10px;
  color: #a4a4a4;
  height: 36px;
  box-sizing: border-box;
}
.border-set {
  border: 1px solid #c10708;
  margin: 40px 0px;
}
.hello-wrapper .input-wrapper input::-webkit-outer-spin-button,
.hello-wrapper .input-wrapper input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.hello-wrapper .input-wrapper input:focus {
  outline: none;
  box-shadow: none;
}
@media (min-width: 320px) and (max-width: 767px) {
  .hello-wrapper {
    width: 94%;
    max-width: 100%;
    margin: 40px auto 0px auto !important;
  }
}
</style>

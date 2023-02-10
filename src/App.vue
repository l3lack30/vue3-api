<script setup>
import axios from "axios";
import { ref } from "vue";

const data = ref();
const config = {
  method: "get",
  url: "https://house-stock-watcher-data.s3-us-west-2.amazonaws.com/data/all_transactions.json",
  headers: {},
};
axios(config)
  .then(function (response) {
    data.value = response.data;
    console.log(data.value);
  })
  .catch(function (error) {
    console.log(error);
  });

</script>
<template>
  <h1>House Stock Watcher API</h1>
  <table class="table-bg">
    <thead>
      <th>Disclosure_year</th>
      <th>Disclosure_date</th>
      <th>Owner</th>
    </thead>
    <tbody>
      <tr v-for="(value, index) in data" :key="index">
        <td>{{ value.disclosure_year }}</td>
        <td>{{ value.disclosure_date }}</td>
        <td>{{ value.owner }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
.table-bg{
  background: rgb(1, 248, 248);
  padding: 10px
  
}
</style>
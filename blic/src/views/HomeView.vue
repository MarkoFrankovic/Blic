<template>
  <div class="home">
    <li v-for="item in items" :key="item.url">
      <router-link :to="{ name: 'about', params: { item } }">{{
        item.url
      }}</router-link>
    </li>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: "HomeView",
  data: function () {
    return {
      items: [],
    };
  },

  async mounted() {
    let podatci = await fetch("http://ntankovic.unipu.hr:8000/api/books");
    let rezultati = await podatci.json();
    this.items = rezultati;
    console.log(rezultati);
  },
};
</script>

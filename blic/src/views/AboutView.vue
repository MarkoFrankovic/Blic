<template>
  <div class="item">
    <h1>Detalji knjige</h1>

    <li>Authori: {{ item.authors }}</li>
    <li>ISBN:</li>
    <li>Broj stranica:</li>
    <li>Izdavač:</li>
    <li>Zemlja podrijetla:</li>
    <li>Broj likova:</li>

    <button>
      <router-link to="/">Natrag</router-link>
    </button>
  </div>
</template>

<script>
export default {
  name: "AboutView",
  data() {
    return {
      item: [],
    };
  },

  async mounted() {
    let podatci = await fetch("http://ntankovic.unipu.hr:8000/api/books");
    let rezultati = await podatci.json();
    this.item = rezultati;
    console.log(rezultati);
  },
};
</script>

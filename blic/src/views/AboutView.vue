<template>
  <div class="item">
    <h1>Detalji knjige</h1>

    <!--
    <li>Authori: {{ item.item.author.authors }}</li>
    <li>ISBN: {{ item.item.ISBN.isbn }}</li>
    <li>Broj stranica: {{ item.item.broj_stranic.authors }}</li>
    <li>Izdavač: {{ item.item.izdavac.publisher }}</li>
    <li>Zemlja podrijetla: {{ item.item.drzava.country }}</li>
    <li>Broj likova: {{ item.item.likovi.characters }}</li>
-->
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

<template>
  <div class="home">
    <li v-for="item in items" :key="item.url">
      <router-link :to="{ name: 'about', params: { items } }">{{
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

  methods: {
    async getData2() {
      let podatci = await fetch("http://ntankovic.unipu.hr:8000/books.json");
      let rezultati = await podatci.json();

      console.log(rezultati);

      let temp = {
        url: rezultati.url,
        ime: rezultati.name,
        ISBN: rezultati.isbn,
        author: rezultati.authors,
        broj_stranica: rezultati.numberOfPages,
        izdavac: rezultati.publisher,
        drzava: rezultati.country,
        mediatype: rezultati.mediatype,
        datum_izdanja: rezultati.released,
        likovi: rezultati.characters,
        povlikovi: rezultati.povCharacters,
      };

      this.items.push(temp);
    },
  },
};
</script>

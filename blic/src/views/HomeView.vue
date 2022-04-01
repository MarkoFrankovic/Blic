<template>
  <div class="home">
    <li v-for="item in items" :key="item.authors">
      <router-link :to="{ name: 'about', params: { item } }">{{
        item.authors
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
    async getData() {
      let podatci = await fetch("https://www.anapioficeandfire.com/api/books");
      let rezultati = await podatci.json();

      console.log(rezultati);

      let temp = {
        ime: rezultati.name,
        ISBN: rezultati.isbn,
        authori: rezultati.authors,
        broj_stranica: rezultati.broj_stranica,
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

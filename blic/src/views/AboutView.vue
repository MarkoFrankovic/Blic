<template>
  <div class="item">
    <h1>Detalji knjige</h1>
    <li>Autori: {{ item.item.author.name }}</li>
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
  props: {
    sha: String,
  },

  data() {
    return {
      item: [],
    };
  },

  methods: {
    async getData() {
      let podatci = await fetch("https://www.anapioficeandfire.com/api/books");
      let rezultati = await podatci.json();

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

      this.item.push(temp);
      console.log(rezultati);
    },
  },
};
</script>

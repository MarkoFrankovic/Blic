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
  props: {
    sha: String,
  },

  data() {
    return {
      item: [],
    };
  },

  async mounted() {
    let podatci = await fetch("http://ntankovic.unipu.hr:8000/api/books");
    let rezultati = await podatci.json();

    console.log(rezultati);

    /*
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
     */
  },
};
</script>

<template>
  <div class="home">

    <ul>

      </ul>

    <ul>
      <!-- u key se stavlja nešto jedinstveno - primary key -->
      <li v-for="item in commits" v-bind:key="item.sha"> Commit:  <router-link :to="'/commit/' + item.sha">{{ item.sha }} </router-link> </li>
      </ul>

  </div>

</template>

<script>
// @ is an alias to /src

// JS Objekt -> ograničen vitičastim {} zagradama -> koji je definicija Vue komponente
export default {
  name: 'HomeView', //string
  data() {
   return {
     // mora vratiti objekt ciji atributi (ime,prezime) su vidljivi HTML template dijelu
     ime: "Niko",
     prezime: "Novak",
     commits: [],
   };
  },
  async mounted(){  //izvršava se kad se komponenta pokreće (funkcija)

              //dohvatamo postove s githuba -> na github adresu
  let rezultat = await fetch("http://localhost:9999/github.json"); 

  let podaci = await rezultat.json()

  // console.log(typeof podaci); //vrsta podataka (array je zbog tip zagrade{} )

  // of - za array
  // in - za objekt
  for (let item of podaci) {
    item:
    console.log(item.sha);
  }
  

  //mora se koristit this da bi se pristupio data
  this.commits = podaci;
  },
};
//Vue.js je poziva

</script>
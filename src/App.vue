<!-- Vue sayfayı 3 ayrır 1-JavaScript -->

<script>
export default {
  data() {
    return {
      message: "Hello world!",
      alinacaklar: ["patates", "domates"],
      urun: "",
      goster: false,
      acikMi: false
    }
  },
  methods: {
    ekle(event) {
      event.preventDefault();
      this.alinacaklar.push(this.urun);
      this.urun = "";
    },
    sil(index, event) {
      event.preventDefault();
      this.alinacaklar.splice(index, 1);
    },
    computed:{
lambaAcmaKapamaMetni: function(){
  return this.acikMi ? "Lambayı Kapat" : "Lambayı Aç";
}
    } 
  }
}
</script>

<!--2--->

<template>
  <h1>Vue Öğreniyorum</h1>Your message:
  <input type="text" v-model="message" />
  <!--v-model ile inputa yazılan message da yazılır-->

  <h2>{{ message }} {{ message }} {{ message }}</h2>

  <hr />

  <h2>Alışveriş Listem</h2>
  <form @submit="ekle">
    Alınacak:
    <input type="text" v-model="urun" />
    <button>Ekle</button>
  </form>

  <ul>
    <li v-for="(alinacak, i) in alinacaklar">
      <!--C# foreach gibi-->
      {{ alinacak }}
      <a href="#" @click="sil(i, $event)">&times</a>
    </li>
  </ul>

  <hr />

  <input type="checkbox" v-model="goster" /> Aşağıdaki paragrafı göster
  <p
    v-if="goster"
  >Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsa doloribus magni, molestias ipsum vero quaerat incidunt magnam unde autem, eos itaque quam distinctio eaque aspernatur consequuntur facere iste soluta consequatur laudantium quis minima beatae rem sint! Facilis modi adipisci laudantium aspernatur dolores corrupti dolorem nesciunt. Ipsum maxime ratione modi iure ullam ipsam, iusto eius explicabo cupiditate voluptates officia sit libero iste aliquam alias. Accusantium recusandae nulla tempora esse consequuntur facilis voluptates numquam rem, neque eos cumque velit non? Possimus quibusdam non dolores enim, dolorum quis. Cupiditate exercitationem quos iste magni perferendis corrupti? Necessitatibus reprehenderit voluptatum quas culpa beatae quisquam sint?</p>
  <!--V-if ile true iste gösteriyor false ise göstermiyor-->

  <hr />

  <!-- <button @click="acikMi = !acikMi">Lambayı {{ acikMi ? "Kapat" : "Aç" }}</button> (aşağıdaki veyukarıdaki component yerine bu da yapılabilri) -->
<button @click="acikMi = !acikMi">
  {{ lambaAcmaKapamaMetni }}
</button>

  <div>
    <img v-if="acikMi" src="./assets/img/on.png" alt="Açık Lamba" width="100" />
    <img v-else src="./assets/img/off.png" alt="Kapali Lamba" width="100" />
  </div>
 
</template>

<!--3-CSS-->
<style>
@import "./assets/base.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;
}
</style>

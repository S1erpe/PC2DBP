<script>
import countries from "/src/datasets/countries.json";
import CountryComponent from "../components/CountryComponent.vue";

export default {
  name: "CapitalsGameView",
  components: {
    CountryComponent,
  },
  data() {
    return {
      country: {},
      capital: "",
      puntaje: 0,
      val : false,

    };
  },
  created() {
    this.country = countries[Math.floor(Math.random() * countries.length)];
  },
  methods: {
    setCapital(e) {
      //TODO: implementar. fija la capital del input.
      this.capital = e.target.value;
    },
    adivinarCapital(e) {
      //TODO: implementar. verifica si la adivinanza es correcta.
      if(e.target.value === this.capital) {
        this.val = true;
      }
      
    },
  },
};
</script>

<template>
  <h1>Puntaje: {{ puntaje }}</h1>
  <div class="countries">
    <!-- TODO: usar los metodos definidos arriba dentro del input para llenar el estado de la capital a adivinar-->
    <input
      placeholder="Adivina la capital"
    />
    <button @click="adivinarCapital">Adivina!</button>
    <div class="countries-container">
      <!--TODO: CREAR EL COMPONENTE PARA VISUALIZAR EL PAIS-->
      <img src = "http://www.countryflagsapi.com/png/{{country.iso3}}" >
      <p>Moneda: {{country.currency_name}} {{country.currency}}</p>
      <br><br>
      <p>Region {{country.region}}</p>
    </div>
  </div>
</template>

<style scoped>
@media (min-width: 1024px) {
  .countries {
    align-items: center;
  }

  input {
    line-height: 2em;
  }

  .countries-container {
    margin-left: 35%;
    align-items: center;
    overflow-y: auto;
    vertical-align: middle;
    padding: 10px;
  }
}
</style>

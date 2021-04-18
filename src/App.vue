<template>
  <div id="app">
    <img src="./assets/logo.png" alt="">
    <div class="campo">{{ tiempo }}</div>
  <div class="m-3">
    <button v-for="btn in data" :key="btn.name" @click="botones(btn.value)" class="m-2 btn btn-outline-secondary">{{btn.name }}</button>
    </div>
    <button @click="clic" class="btn btn-primary">Comenzar</button>
    <button @click="parar" class="btn btn-success">Detener</button>
    
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      tiempo: 10,
      intervalo: "",
      data: [{
        name: "3s",
        value: "3"
      },
      {
        name: "1m",
        value: "60"
      },
      {
        name: "5m",
        value: "300"
      },
      {
        name: "10m",
        value: "600"
      },
      {
        name: "30m",
        value: "1800"
      },  
      ]
    }
  },
  watch: {
    tiempo(v) {
      if(v === 0) this.parar();
    }
  },
  methods: {
    clic() {
      this.intervalo = setInterval(() => {
        this.tiempo--
      }, 1000);
      
    },
    parar() {
      clearInterval(this.intervalo);
      this.tiempo = 10;
    },
    botones(v) {
      console.log(v);
      this.tiempo = v;
    } 
  },
  
};


</script>




<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.campo {
  font-size: 1rem;
  border: solid 1px #2c3e50;
  border-radius: 12px;
  max-width: 4rem;
  padding: .5rem 1rem;
  margin: 0 auto;
}

.btn{
  margin: 1rem 1rem;
}
</style>

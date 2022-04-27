<template>
  <div>
    <h1>Cálculo do IMC</h1>
    <h2>Digite seu peso e altura para calcular seu IMC</h2>

    <div class="div-imc">
      <span class="p-float-label">
        <InputText id="peso" type="text" v-model="peso" />
        <label for="peso">Peso</label>
      </span>
    </div>

    <div class="div-imc">
      <span class="p-float-label">
        <InputText id="altura" type="text" v-model="altura" />
        <label for="altura">Altura</label>
      </span>
    </div>

    <div class="div-imc">
      <BtnCalcula id="btncaclc" label="Calcular" @click="calculate" />
      <BtnCalcula label="Limpar" @click="clear" id="btncaclc" />
    </div>

    <div>
      <p v-if="imc > 0">Seu imc: {{imc}}</p>
      <p v-if="classificacao != ''">Classificação do imc: {{classificacao}}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      altura: null,
      peso: null,
      imc: 0,
      classificacao: "",
    };
  },
  methods: {
    calculate() {
      this.imc = (this.peso / (this.altura * this.altura)).toFixed(2);
      if (this.imc < 18.5) {
        this.classificacao = 'Magreza';
      }else if (this.imc >= 18.5 && this.imc < 25){
        this.classificacao = 'Normal';
      }else if (this.imc >= 25 && this.imc < 30){
        this.classificacao = 'Sobrepeso';
      }else if (this.imc >= 30 && this.imc < 40){
        this.classificacao = 'Obesidade';
      }else{
        this.classificacao = 'Obesidade Grave'
      }  
    },
    clear(){
      this.altura= null;
      this.peso= null;
      this.imc= 0;
      this.classificacao = "";
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
.div-imc {
  margin-top: 2rem;
  margin-left: 2rem;
}
h1 {
  font-size: 2rem;
}
h2 {
  font-size: 1.1rem;
}
#btncaclc{
  margin-right: 10px;
  padding: 10px;
}
</style>

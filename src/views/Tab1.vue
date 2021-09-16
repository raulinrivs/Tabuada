<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tabuada</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true" id="app">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab1</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-grid>
        <ion-row>
          <p>{{mensagem}}</p>
        </ion-row>
        <ion-row>
          <ion-input v-model="numero" type="num" id="numero" placeholder="Digite um numero de 1 a 10"></ion-input>
          <ion-button v-on:click="criarTabuada()">Enviar</ion-button>  
        </ion-row>
      </ion-grid>
      <ion-grid>
        <ul>
            <li v-for="item in numeros" :key="item">
                {{ item.numero }} x {{ item.multiplicador }} = {{item.resultado}}
            </li>
        </ul>
      </ion-grid>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton, IonGrid, IonRow, IonInput } from '@ionic/vue';
import { defineComponent } from 'vue';

export default  defineComponent({
  name: 'Tab1',
  components: {IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage, 
    IonButton, 
    IonGrid, 
    IonRow, 
    IonInput },
  data() {
    return {
      mensagem: 'Insira um numero...',
      numero: 0,
      numeros: [{numero:0, multiplicador:0, resultado:0}]
    }
  },
  methods: {
    criarTabuada(){
      this.numeros = [{numero:this.numero, multiplicador:0, resultado:0}]
      for(let i=1; i<=10; i++){
        this.numeros.push({numero:this.numero, multiplicador:i, resultado:this.numero * i})
      }
      console.log(this.numeros)
    }
  }
})
</script>

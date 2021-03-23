<template>
<h1>Veille techno</h1>
<Form @add="saveTechno"/>
<br>

<!-- sans les deux points devant technos , on aurait passer au composant une string , là on passe bien la valeur -->
<TechnoList :technos="technos" @delete-techno="deleteTechno"/>
</template>


<script>

import Form from "@/components/Form";
import TechnoList from "@/components/TechnoList";

import { ref } from '@vue/reactivity';
export default {
  name: 'App',
  components: {
    Form,
    TechnoList
  },
  setup() {
    let technos = ref([]);

    const saveTechno = function(data) {

      technos.value = [...technos.value, { techno : data , id : Date.now()}];

};
        const deleteTechno = function (tech) {
          // console.log('app2',technos.value);
          // console.log('app', tech);
          // pour chaque "tec" dans le tableau de technos.value tu regardes s'il est différent du tech ligne 31 , s'il est différent on l'affiche
          technos.value = technos.value.filter(tec => tec.id !== tech.id);

  };
return {
    saveTechno,
    deleteTechno,
    technos,
    }

  },
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
<h1>Veille techno</h1>
<Form @add="saveTechno"/>
<br>

<!-- sans les deux points devant technos , on aurait passe au composant une string , là on passe bien la valeur -->
<TechnoList :technos="technos" @delete-techno="deleteTechno" @edit-techno="editTechno"/>
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
  // ici "tech" est le payload du custom event du composant Technolist "edit-techno"
  // littéralement on traduit le map par , sur l'element courant de ta boucle , donc tec ,
  //  je te demande si tec.id et tech ( le tech de technolist ) sont différent , alors tu fais la modif , sinon tu touches à rien 
        const editTechno = function(tech) {
          technos.value = technos.value.map(tec => tec.id !== tech.id ? tec : tech);
        }

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
    editTechno
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

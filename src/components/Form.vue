<template>
  <form @submit.prevent="addTechno">
    <label for="techno">Techno à ajouter</label>
    <br>
    <input type="text" name="techno" v-model="techToLearn">
    <br>
    <button type="submit" >ajouter</button>
  </form>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {
          setup(props, context){
            let techToLearn = ref("") ;

            const addTechno = function() {
              console.log("Form | addTechno() | techToLearn" , techToLearn);
              // emit , avec le deuxieme parametre de setup , context , permet de passer la saisie de l'utilisateur au composant APP , le composant parent
              context.emit("add", techToLearn.value);
              techToLearn.value = "";

}
return {
  techToLearn,
  addTechno,

    }
  }
}
</script>

<style>

</style>
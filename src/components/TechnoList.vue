<template>
<h3>TechnoList</h3>
{{technos.length}} techno{{technos.length > 1 ? "s" : ""}}
<ul>
  <li v-for="tech in technos" :key="tech.id">
    <button @click="editTechno(tech)">Editer</button>
    <button @click="deleteTechno(tech)">Supprimer</button> 
    <span v-if="technoToEdit !== null && technoToEdit.id === tech.id">
      <input type="text" v-model="technoToEdit.techno"><button @click="save">sauvegarder</button>
    </span>
    <span v-else>{{tech.techno}}</span>
    </li>
</ul>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {
  emits : ["delete-techno"],
  props: {
    technos : {
      type : Array,
      required : true,

    }
  },
  // au lieu de déclarer context puis faire context.emit on passe directement emit en destructure en deuxieme argument
  setup(props, {emit}){
    let technoToEdit = ref(null);

    let deleteTechno = function(tech) {
      emit("delete-techno", tech);

    };
    let editTechno = function(tech) {
      technoToEdit.value = tech;
    };
    let save = function() {
      technoToEdit.value = null;
    }
    return{
      deleteTechno,
      editTechno,
      save,
      technoToEdit,
    }
  }
}
</script>

<style>
ul{
  list-style: none;
}
</style>
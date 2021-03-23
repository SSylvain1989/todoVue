<template>
<h3>TechnoList</h3>
{{technos.length}} techno{{technos.length > 1 ? "s" : ""}}
<ul>
  <li v-for="tech in technos" :key="tech.id"><button @click="deleteTechno(tech)">Supprimer</button> {{tech.techno}}</li>
</ul>
</template>

<script>
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
    let deleteTechno = function(tech) {
      emit("delete-techno", tech);

    }
    return{
      deleteTechno,
    }
  }
}
</script>

<style>
ul{
  list-style: none;
}
</style>
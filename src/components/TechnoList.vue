<template>
<h3>TechnoList</h3>
{{technos.length}} techno{{technos.length > 1 ? "s" : ""}}
<ul>
  <li v-for="tech in technos" :key="tech.id">{{tech.techno}}</li>
</ul>
</template>

<script>
export default {
  props: {
    technos : {
      type : Array,
      required : true,

    }
  }
}
</script>

<style>
ul{
  list-style: none;
}
</style>
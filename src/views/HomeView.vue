<template>
  <div class="home">
    <h1 class="mt-10">Lista de Cursos</h1>
        <CardComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import CardComponent from '@/components/CardComponent.vue';
import { mapState } from 'vuex';
export default {
  name: 'HomeView',
  components: {
    CardComponent
  },
  computed:{
    ...mapState("[cursos]")
  }
}
</script>

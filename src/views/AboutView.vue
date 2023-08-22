<template>
  <div class="about">
    <v-col>
      <h1 class="mt-10">Administracion</h1>
        <AddCourseComponent class="mt-5"/>   
    </v-col>
    <v-col>
      <ListComponent />
    </v-col>
  </div>
</template>
<script>
import ListComponent from '@/components/ListComponent.vue';
import AddCourseComponent from '@/components/AddCourseComponent.vue';
export default {
  components: {
    ListComponent,
    AddCourseComponent
  }
}
</script>

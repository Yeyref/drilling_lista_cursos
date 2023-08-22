<template>
    <div>
        <MigaComponent/>
        <v-col>
      <h1 class="mt-10">EDITAR CURSO</h1>
        <EditCourseComponent class="mt-5"/>   
        </v-col>
    </div>
</template>

<script>
import MigaComponent from '@/components/MigaComponent.vue';
import EditCourseComponent from '@/components/EditCourseComponent.vue';
    export default {
        components:{
            MigaComponent,
            EditCourseComponent
        }
    }
</script>

<style lang="scss" scoped>

</style>
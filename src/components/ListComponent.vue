<template>
  <div>
    
    <v-app id="inspire">
      <v-simple-table>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-center">
                Curso
              </th>
              <th class="text-center">
                Cupos
              </th>
              <th class="text-center">
                Inscritos
              </th>
              <th class="text-center">
                Duracion
              </th>
              <th class="text-center">
                Costo
              </th>
              <th class="text-center">
                Terminado
              </th>
              <th class="text-center">
                Fecha
              </th>
              <th class="text-center">
                Acciones
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(curso, index) in cursos" :key="index">
              <td>{{ curso.nombre }}</td>
              <td>{{ curso.cupos }}</td>
              <td>{{ curso.inscritos }}</td>
              <td>{{ curso.duracion }}</td>
              <td class="rounded-bg-green">$ {{ curso.costo }}</td>
              <td class="rounded-bg-gray" v-if="curso.completado == false"> No</td>
              <td class="rounded-bg-blue" v-else>Si</td>
              <td class="rounded-bg-green">{{ curso.fecha_registro }}</td>
              <td>
                <v-btn color="yellow" @click="set_id_product_id(curso.id), redirigir()">
                  <v-icon>mdi-pencil</v-icon>
                </v-btn>
                <v-btn color="red" @click="remove(curso, index)">
                  <v-icon>mdi-delete</v-icon>
                </v-btn>
              </td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
      <div>
        <v-divider class="mt-7 mb-7"></v-divider>
       
        <v-alert class="text-left" dense outlined color="purple">
          <v-icon color="purple">mdi-account-multiple</v-icon>
          Cantidad total de alumnos permitidos: <strong>190</strong> alumnos
        </v-alert>
        <v-alert class="text-left" dense outlined color="blue">
          <v-icon color="blue">mdi-account-check</v-icon>
          Cantidad total de alumnos inscritos: <strong>103</strong> alumnos
        </v-alert>
        <v-alert class="text-left" dense outlined color="deep-orange">
          <v-icon color="deep-orange">mdi-account-plus</v-icon>
          Cantidad total de cupos restantes: <strong>87</strong> alumnos
        </v-alert>
        <v-alert class="text-left" dense outlined color="pink">
          <v-icon color="pink">mdi-cancel</v-icon>
          Cantidad total de cursos terminados: <strong>2</strong> cursos
        </v-alert>
        <v-alert class="text-left" dense outlined color="light-green">
          <v-icon color="light-green">mdi-bell-ring</v-icon>
          Cantidad total de cursos activos: <strong>4</strong> cursos
        </v-alert>
        <v-alert class="text-left" dense outlined color="amber">
          <v-icon color="amber">mdi-bell-ring</v-icon>
          Cantidad total de cursos: <strong>6</strong> cursos
        </v-alert>
      </div>
    </v-app>

  </div>
</template>

<script>
import { mapState, mapActions } from 'vuex';
export default {
  name: 'CarouselComponent',
  // props: {},
  data: function () {
    return {

    }
  },
  computed: {
    ...mapState(["cursos"]),
  },
  methods: {
    ...mapActions(["set_id_product_id"]),
    redirigir() {
      this.$router.push('/EditarCurso');
    },
    remove(product) {
      let response = confirm(
        `¿Esta seguro de eliminar el curso con el nombre ${product.nombre} ?`
      );
      if (response) {
        this.$store.dispatch("remove_product", product.id);
      }
    },
  },
  // watch: {},
  components: {
  },
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped>
.rounded-bg-green {
  color: white;
  background-color: #4CAF50;
  border-radius: 30px;
  padding-left: 0;
  padding-right: 0;

}

.rounded-bg-blue {
  color: white;
  background-color: #1dcaf1;
  border-radius: 30px;

}

.rounded-bg-gray {
  color: white;
  background-color: #839fa5;
  border-radius: 30px;

}
</style>
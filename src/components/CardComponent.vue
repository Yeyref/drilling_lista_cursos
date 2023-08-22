<template>
  <div>
    <v-row>
      <v-col md="4" v-for="(curso, index) in cursos" :key="index.id">
        <v-app id="inspire">
          <v-card :loading="loading" class="mx-auto my-12" width="70%">
            <template slot="progress">
              <v-progress-linear color="deep-purple" height="10" indeterminate></v-progress-linear>
            </template>

              <v-img height="350" :src="curso.img"></v-img>
            
            <v-card-title>{{ curso.nombre }}</v-card-title>

            <v-card-text>
              <p>Informacion</p>
              <v-timeline align-top dense>

                <v-timeline-item color="purple" medium>
                  <v-row class="pt-1">
                    <v-col cols="8">
                      <p>Costo: <strong>{{ curso.costo }}</strong> </p>
                      <p>Duracion: {{ curso.duracion }}
                      </p>
                    </v-col>
                  </v-row>
                </v-timeline-item>

                <v-timeline-item color="green" medium>
                  <v-row class="pt-1">
                    <v-col cols="8">
                      <p>Cupos: <strong>{{ curso.cupos }}</strong></p>
                      <p v-if="curso.completado == false">
                        Completado: No </p>
                      <p v-else>
                        Completado: Si
                      </p>
                    </v-col>
                  </v-row>
                </v-timeline-item>

                <v-timeline-item color="purple" medium>
                  <v-row class="pt-1">
                    <v-col cols="8">
                      <p>Fecha de Registro:</p>
                      <p>{{ curso.fecha_registro }}</p>
                    </v-col>
                  </v-row>
                </v-timeline-item>

                <v-timeline-item color="green" medium>
                  <v-row class="pt-1">
                    <v-col cols="8">
                      <p>Descripcion:</p>
                      <p>{{ curso.descripcion }}</p>
                    </v-col>

                  </v-row>
                </v-timeline-item>
              </v-timeline>
            </v-card-text>
          </v-card>
        </v-app>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  name: 'CardComponent',
  // props: {},
  data: function () {
    return {
      loading: false,
      selection: 1,
    }
  },
  computed: {
    ...mapState(["cursos"])
  },
  methods: {
    reserve() {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    },

  },
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
}
</script>

<style scoped></style>
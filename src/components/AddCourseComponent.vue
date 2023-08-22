<template>
    <div>
        
            <v-row justify="center">
                <v-dialog v-model="dialog" persistent max-width="600px">
                    <template v-slot:activator="{ on, attrs }">
                        <v-btn color="primary" dark v-bind="attrs" v-on="on">
                            Agregar Curso
                        </v-btn>
                    </template>
                    <v-card>
                        
                        <v-card-text>
                            <v-container>
                                <v-row>
                                    <v-col cols="12">
                                        <v-text-field label="Nombre" v-model="formCurso.nombre" required></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field label="URL de la imagen" v-model="formCurso.img"
                                            hint="example of helper text only on focus"></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field label="Cupos del curso" v-model="formCurso.cupos" hint="example of persistent helper text"
                                            persistent-hint required></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field label="Inscritos en el curso" v-model="formCurso.inscritos" required></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field label="Duracion del curso" v-model="formCurso.duracion"  required></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field label="Fecha de registro" v-model="formCurso.fecha_registro" required></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field label="Costo del curso" v-model="formCurso.costo" required></v-text-field>
                                    </v-col>
                                    <v-col cols="12">
                                        <v-text-field
                                            v-model="formCurso.descripcion"
                                            label="Descripcion del curso"
                                            placeholder="Ingresa tu texto"
                                            outlined
                                        ></v-text-field>
                                    </v-col>
                                </v-row>
                            </v-container>
                            <small>*indicates required field</small>
                        </v-card-text>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                             <v-btn color="green" class="white--text"  @click="addProduct">
                                Agregar
                            </v-btn>
                            <v-btn color="orange" class="white--text"  @click="dialog = false">
                                Limpiar Formulario
                            </v-btn>
                            <v-btn color="red lighten-1" class="white--text"  @click="dialog = false">
                                Cancelar
                            </v-btn>
                           
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </v-row>
    
    </div>
</template>

<script>
export default {
    name: 'AddCourseComponent',
    // props: {},
    data: function () {
        return { 
            dialog: false,
            
            formCurso:{
                nombre:'',
                img:'',
                cupos:'',
                inscritos:'',
                duracion:'',
                costo:'',
                completado: false,
                fecha_registro:'',
                descripcion:''
            }
        }
    },
    // computed: {},
    mounted() {
    this.obtenerFechaActual();
  },
    methods: {
        obtenerFechaActual() {
      const fecha = new Date();
      const dia = fecha.getDate();
      const mes = fecha.getMonth() + 1; // Los meses en JavaScript van de 0 a 11
      const año = fecha.getFullYear();

      this.formCurso.fecha_registro = `${dia}/${mes}/${año}`;
    },
    addProduct() {
      if (
        this.formCurso.nombre != "" &&
        this.formCurso.img != "" &&
        this.formCurso.cupos != "" &&
        this.formCurso.inscritos != "" &&
        this.formCurso.duracion != "" &&
        this.formCurso.costo != "" &&
        this.formCurso.descripcion != "" &&
        this.formCurso.fecha_registro != ""
      ) {
        let data = { ...this.formCurso};
        this.$store.dispatch("add_product", data);
        this.clean();
      }
    },
    clean() {
        this.formCurso.nombre = "";
        this.formCurso.img = "";
        this.formCurso.cupos = "";
        this.formCurso.inscritos = "";
        this.formCurso.duracion = "";
        this.formCurso.costo = "";
        this.formCurso.descripcion = "";
    },
    },
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},

    // -- End Lifecycle Methods
}
</script>

<style scoped></style>
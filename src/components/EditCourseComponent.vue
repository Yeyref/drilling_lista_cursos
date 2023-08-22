<template>
    <div>
        <v-container>
            <v-form ref="form" lazy-validation>
                <v-text-field v-model="formCurso.nombre" :counter="10"  label="Nombre"
                    required></v-text-field>

                <v-text-field v-model="formCurso.img" :counter="10"  label="URL de la imagen"
                    required></v-text-field>

                <v-text-field v-model="formCurso.cupos" :counter="10"  label="Cupos del curso"
                    required></v-text-field>

                <v-text-field v-model="formCurso.inscritos" :counter="10" label="Inscritos en el curso"
                    required></v-text-field>

                <v-text-field v-model="formCurso.duracion" :counter="10"  label="Duracion del curso"
                    required></v-text-field>

                <v-text-field v-model="formCurso.fecha_registro" label="Fecha de registro"
                    required></v-text-field>

                <v-text-field v-model="formCurso.completado" :counter="10"  label="Terminado"
                    required></v-text-field>

                <v-text-field v-model="formCurso.costo" :counter="10" label="Costo del curso"
                    required></v-text-field>

                <v-text-field v-model="formCurso.descripcion" label="Descripcion del curso" placeholder="Ingresa tu texto"
                    outlined></v-text-field>




                <v-btn color="blue" class="mr-4" @click="update">
                    Actualizar
                </v-btn>

                <v-btn color="green" class="mr-4" @click="redirigir">
                    ir a la lista
                </v-btn>

               

            </v-form>
        </v-container>
    </div>
</template>

<script>
import { mapState, mapGetters, mapActions } from "vuex";
export default {
    name: 'EditCourseComponent',
    // props: {},
    data: function () {
        return {
            formCurso: {
                nombre: '',
                img: '',
                cupos: '',
                inscritos: '',
                duracion: '',
                costo: '',
                completado: false,
                fecha_registro: '',
                descripcion: ''
            }
        }
    },
    computed: {
        ...mapState(["id_product_id"]),
        ...mapGetters(["getProductById"]),
    },
    methods: {
        ...mapActions(["edit_product"]),
        updated() {           
                if (
                this.formCurso.nombre != "" &&
                this.formCurso.img != "" &&
                this.formCurso.cupos != "" &&
                this.formCurso.inscritos != "" &&
                this.formCurso.duracion != "" &&
                this.formCurso.costo != "" &&



                
                this.formCurso.completado != "" &&
                this.formCurso.fecha_registro != "" &&
                this.formCurso.descripcion != ""
            ) {
                let data = { ...this.formCurso, id: this.id_product_id };
                this.edit_product(data);
                
            }
        }, 
         
        redirigir(){
            this.$router.push('/about');
        },

        clean() {
            this.formCurso.nombre = "";
            this.formCurso.img = "";
            this.formCurso.cupos = "";
            this.formCurso.inscritos = "";
            this.formCurso.duracion = "";
            this.formCurso.costo = "";
            this.formCurso.fecha_registro = "";
            this.formCurso.descripcion = "";
        },
        setProduct() {
            let prod = this.getProductById(this.id_product_id);
            this.formCurso.nombre = prod.nombre;
            this.formCurso.img = prod.img;
            this.formCurso.cupos = prod.cupos;
            this.formCurso.inscritos = prod.inscritos;
            this.formCurso.duracion = prod.duracion;
            this.formCurso.costo = prod.costo;
            this.formCurso.descripcion = prod.descripcion;
            this.formCurso.fecha_registro = prod.fecha_registro;
        },
    
    },
    mounted: function () {
        this.setProduct();
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
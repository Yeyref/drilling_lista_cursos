<template>
    <div id="app">
        <v-breadcrumbs :items="items">
            <template v-slot:item="{ item }">
                <v-breadcrumbs-item :href="item.href" :disabled="item.disabled">
                    {{ item.text.toUpperCase() }}
                </v-breadcrumbs-item>
            </template>
        </v-breadcrumbs>
    </div>
</template>

<script>
export default {
    name: 'MigaComponent',
    // props: {},
    data: function () {
        return {
            items: [
                {
                    text: 'Administracion',
                    disabled: false,
                    href: '/About',
                },
                {
                    text: 'Editar Curso',
                    disabled: true,
                    href: '/EditarCurso',
                },
            ]
        }
    },
    // computed: {},
    //methods: {},
    // watch: {},
    // components: {},
    // mixins: [],
    // filters: {},
    // -- Lifecycle Methods
    // -- End Lifecycle Methods
}
</script>

<style scoped></style>
<template>
    <v-app>
        <v-card class="mx-auto overflow-hidden" height="100%" width="100%">
            <v-app-bar color="purple" dark>
                <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

                <v-toolbar-title>Cursos AlfaWeb</v-toolbar-title>
            </v-app-bar>

            <v-navigation-drawer v-model="drawer" absolute temporary>
                <v-list nav dense>
                    <v-list-item-group v-model="group" active-class="deep-purple--text text--accent-4">
                        <v-list-item>
                            <v-list-item-icon>
                                <v-icon>mdi-home</v-icon>
                            </v-list-item-icon>

                            <v-list-item-title>
                                <router-link to="/">Home</router-link>
                            </v-list-item-title>

                        </v-list-item>

                        <v-list-item>
                            <v-list-item-icon>
                                <v-icon>mdi-wrench</v-icon>
                            </v-list-item-icon>
                            <v-list-item-title>
                                <router-link to="/about">Administracion</router-link>
                            </v-list-item-title>
                        </v-list-item>

                    </v-list-item-group>
                </v-list>
            </v-navigation-drawer>
            <router-view /> 
        </v-card>
    </v-app>
</template>

<script>
export default {
    data: () => ({
        drawer: false,
        group: null,
    }),
}
</script>
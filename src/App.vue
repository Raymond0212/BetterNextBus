<template>
    <div id="app">
        <v-app>
            <router-view/>
            <v-footer
                    color="grey lighten-3"
                    padless
            >
                <v-row
                        justify="center"
                        no-gutters

                >
                    <v-btn
                            @click="$router.push({
                    name: 'bus-list',
                    params: {bus_stop_name: $store.state.stop_selected}
                    })"
                            class="my-2"
                            color="teal"
                            text
                    >
                        Home
                    </v-btn>
                    <v-btn
                            class="my-2"
                            color="teal"
                            text
                            to="/settings"
                    >
                        Settings
                    </v-btn>
                    <v-btn
                            class="my-2"
                            color="teal"
                            text
                            to="/about"
                    >
                        About
                    </v-btn>
                    <v-col
                            class="grey lighten-3 py-4 text-center teal--text caption"
                            cols="12"
                    >
                        <strong>NUSBuses</strong> <br>
                        Made with 💗 by
                        <a :href="github_url" style="color: teal" target="_blank">
                            <strong>@BetterNextBus</strong>
                        </a>
                        <br>Copyright © 2019 - {{new Date().getFullYear()}}
                    </v-col>
                </v-row>
            </v-footer>
        </v-app>
    </div>
</template>

<script>
    import {GITHUB_URL} from "@/utils/config";

    export default {
        data() {
            return {
                github_url: GITHUB_URL
            };
        },
        mounted() {
            this.$store.commit("initializeSettings");
            if (this.$store.state.enable_analytics === true) {
                this.$ga.enable();
            } else {
                this.$ga.disable();
            }
        }
    };
</script>
<style>

</style>

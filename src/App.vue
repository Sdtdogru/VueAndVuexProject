<template>
    <div id="app">


        <nav class="navbar navbar-expand-lg navbar-light bg-light">

            <router-link class="navbar-brand" to="/">ALIŞVERİŞ</router-link>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                    aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">


                    <li class="nav-item dropdown">
                        <router-link class="nav-link  " @click="getCategors" :to="{path:'/category/1'}" role="button"
                                     data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"> ERKEK
                        </router-link>

                    </li>
                    <li class="nav-item dropdown">
                        <router-link class="nav-link  " :to="{path:'/category/2'}" role="button" data-toggle="dropdown"
                                     aria-haspopup="true" aria-expanded="false">KADIN
                        </router-link>


                    </li>
                    <li class="nav-item dropdown">

                        <router-link class="nav-link  " :to="{path:'/category/3'}" role="button" data-toggle="dropdown"
                                     aria-haspopup="true" aria-expanded="false">EV & EŞYA
                        </router-link>
                    </li>
                    <li class="nav-item dropdown">

                        <router-link class="nav-link  " :to="{path:'/category/4'}" role="button" data-toggle="dropdown"
                                     aria-haspopup="true" aria-expanded="false">KOZMETİK
                        </router-link>
                    </li>
                    <li class="nav-item dropdown">

                        <router-link class="nav-link  " :to="{path:'/category/5'}" role="button" data-toggle="dropdown"
                                     aria-haspopup="true" aria-expanded="false">ELEKTRONİK
                        </router-link>
                    </li>

                    <li class="nav-item dropdown">
                        <router-link class="nav-link btn btn-warning   " :to="{path:'/sepetim'}" role="button"
                                     data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            Sepetim {{sepet.length}}
                        </router-link>
                    </li>

                </ul>
                <form class="form-inline my-2 my-lg-0">
                    <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Arama</button>
                </form>
            </div>

        </nav>
        <router-view/>
    </div>
</template>
<script>
    import {mapState} from "vuex"

    export default {
        name: "App",
        computed: {
            ...mapState(["movies", "sepet"]),
            productList() {
                return `${this.movies.id}`
            }
        },
        props: {},
        methods: {
            getCategors() {
                const categoryId = this.$route.params.id;
                this.$store.dispatch('getCategory', categoryId).then(() => {
                    console.log(this.category)
                });

            },
            watch: {
                '$route': 'created'
            }
        }

    }
</script>
<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

</style>

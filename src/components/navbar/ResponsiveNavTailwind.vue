<template>
    <nav class="w-full h-14 bg-indigo-600">
        <ul class="absolute -left-32 top-14 w-48 sm:inset-0 sm:w-full sm:relative bg-indigo-600 flex flex-col sm:flex-row items-center shadow-lg h-full " ref="nav">
            <figure class="fixed top-2 left-2 sm:relative sm:inset-0 image-logo cursor-pointer" @click="toggleNav">
                <img :src="imagePath" class="h-10 w-10">
            </figure>
            <li class="hover:bg-indigo-900 py-4 px-6"
                v-for="(link, index) in navLinks"
                :key="index"
                >
                
                <router-link
                :to="link.path"
                :style="{color : linkColor || '#DDD'}"
                >
                {{link.text}}
            </router-link>
            </li>
        </ul>
    </nav>
</template>

<script>
    export default {
        props: ["background", "linkColor", "hoverBackground", "imagePath"],
        computed: {
            navLinks(){
                return [
                    {text: "Home", path: ""},
                    {text: "About", path: ""},
                    {text: "Contact", path: ""},
                    {text: "Profile", path: ""},
                    {text: "Jobs", path: ""}
                ]
            }
        },
        methods: {
            toggleNav() {
                const nav = this.$refs.nav.classList
                nav.contains("active") ? nav.remove("active") : nav.add("active")
            }
        }
    }
</script>

<style scoped>

    @media only screen and (max-width: 759px){
        ul.active {
            left: 0px;
        }
    }
</style>
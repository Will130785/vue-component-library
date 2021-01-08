<template>
    <nav :style="{background: background || '#333'}">
        <ul :style="{background: background || '#333'}" ref="nav">
            <figure class="image-logo" @click="toggleNav">
                <img :src="imagePath" height="40px" width="40px">
            </figure>
            <li
                v-for="(link, index) in navLinks"
                :key="index"
                @mouseenter="$event.currentTarget.style.background = hoverBackground || '#199'"
                @mouseleave="$event.currentTarget.style.background = background || '#333'">
                
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
    nav {
        height: 60px;
        width: 100%;
    }

    ul {
        margin-block-start: 0;
        margin-block-end: 0;
        padding-inline-start: 0;
        display: flex;
        height: 100%;
        align-items: center;
        box-shadow: 2px 2px 2px #CCC;
    }

    figure {
        cursor: pointer;
    }

    a {
        text-decoration: none;
        display: flex;
        flex-direction: row-reverse;
        align-items: center;
    }

    li {
        list-style-type: none;
        padding: 10px 20px;
    }

    /* i {
        margin-right: 10px;
        font-size: 20px;
    } */

    @media only screen and (max-width: 759px){
      
        ul {
            position: absolute;
            width: 300px;
            flex-direction: column;
            left: -240px;
            transition: 300ms ease all;
            top: 60px;
        }

        ul.active {
            left: 0px;
        }

        figure {
            position: fixed;
            z-index: 1;
            top: 10px;
            left: 2px;
        }

        li {
            width: 100%;
            padding-left: 0;
            padding-right: 0;
        }

        a {
            flex-direction: row;
            margin-left: 20px;
            justify-content: space-between;
            margin-right: 13px;
        }
       
    }
</style>
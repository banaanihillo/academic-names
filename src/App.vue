<template>
    <div id="app">
        <h1> Names </h1>
        <Names />
    </div>
</template>

<script>
    import Names from "./components/Names.vue";

    export default {
        name: "App",
        components: {
            Names
        },
    };
</script>

<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: deeppink;
    }

    html {
        background-color: black;
    }
</style>

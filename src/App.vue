<template>
<div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <Game />
</div>
</template>

<script>
import Game from './components/Game'
export default {
    name: 'App',
    components: {
        Game
    }
}
</script>

<style>
#app {
    font-family: 'Russo One', sans-serif;
    font-size: 24px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #ffffff;
    margin-top: 60px;
}
body {
    background-image: url("https://png.pngtree.com/thumb_back/fw800/background/20191009/pngtree-vintage-pastel-watercolor-background-image_318909.jpg");
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
</style>
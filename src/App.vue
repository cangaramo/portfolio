<template>
    <div id="app">
        <div>
            <router-view />
        </div>
    </div>
</template>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #292929;
    //background-color: #f5f5f5;
    height: 100vh;
    // overflow-y: scroll;
    // overflow-x: hidden;
    font-family: 'Raleway', sans-serif;
}
html {
    //height: 100vh;
    margin: 0;
    padding: 0;
    // overflow: hidden;
}

body {
    margin: 0;
    background-image: url('./assets/background.png');
    background-repeat: no-repeat;
    background-size: cover;
    background-repeat: repeat;
}

//Container
@media (min-width: 576px) {
    .container,
    .container-sm {
        max-width: 610px;
    }
}
@media (min-width: 768px) {
    .container,
    .container-md,
    .container-sm {
        max-width: 800px;
    }
}
@media (min-width: 992px) {
    .container,
    .container-lg,
    .container-md,
    .container-sm {
        max-width: 1020px;
    }
}
@media (min-width: 1200px) {
    .container,
    .container-lg,
    .container-md,
    .container-sm,
    .container-xl {
        max-width: 1200px;
    }
}
</style>

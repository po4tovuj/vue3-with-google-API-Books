<template>
    <nav class="nav-list">
        <router-link class="nav-list__btn" exact to="/">Books List</router-link>
    </nav>
    <router-view />
</template>

<style lang="scss">
html {
    height: 100%;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    height: 100%;
}
body {
    margin: 0;
    height: 100%;
}
.nav-list {
    padding: 30px;
    text-align: left;
    background-color: rgba($color: #000000, $alpha: 0.1);
    display: flex;
    justify-content: space-between;
    &__btn {
        display: inline-block;
        font-weight: bold;
        background-color: #fff;
        color: #000;
        text-decoration: none;
        border: 1px solid grey;
        border-radius: 5px;
        padding: 8px 20px;
        &:hover,
        &.router-link-exact-active {
            background-color: blue;
            color: white;
            border-color: #fff;
        }
    }
}
</style>

<template>
    <div id="app">
        <nav id="nav" class="navbar navbar-expand-lg navbar-dark bg-dark">
            <div class="container-fluid">
                <ul class="navbar-nav">
                    <li class="nav-item">
                        <router-link class="nav-link active" to="/" tag="a"
                            >Overview</router-link
                        >
                    </li>
                    <li class="nav-item">
                        <router-link
                            class="nav-link active"
                            to="/create"
                            tag="a"
                            >Create</router-link
                        >
                    </li>
                </ul>
            </div>
        </nav>
        <router-view />
    </div>
</template>

<style>
html {
    background-color: #1f2833;
}

#app {
    color: #ffffff;
    background-color: #1f2833;
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

#nav a.router-link-exact-active {
    color: #66fcf1;
}

nav a {
    font-weight: bold;
}
</style>

<template>
    <header id="header" class="d-flex align-items-center">
        <div class="container d-flex align-items-center justify-content-between">
            <a href="/" class="logo">
                <img src="/img/logo.png" alt="Vasak Group" title="Vasak Group">
            </a>

            <nav id="navbar" class="navbar">
                <ul>
                    <li>
                        <RouterLink class="router-link-active router-link-exact-active nav-link" to="/">Home</RouterLink>
                    </li>
                </ul>
                <em class="fa fa-list mobile-nav-toggle"></em>
            </nav>
        </div>
    </header>
</template>

<script>
import { RouterLink } from 'vue-router'

export default {
    components: {
        RouterLink
    }
}
</script>

<style scoped>
header{
    margin-bottom: 30px;
}
</style>
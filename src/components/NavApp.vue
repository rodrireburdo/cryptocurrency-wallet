<template>
    <nav class="nav">
        <ul>
            <li><router-link to="/initial" active-class="active">Tus Criptomonedas</router-link></li>
            <li><router-link to="/buy-crypto" active-class="active">Comprar</router-link></li>
            <li><router-link to="/sell-crypto" active-class="active">Vender</router-link></li>
            <li><router-link to="/history" active-class="active">Historial</router-link></li>
        </ul>
    </nav>
</template>

<script setup>
</script>

<style scoped lang="scss">
.nav {
    background-color: $primary-color;
    padding: 15px;
    font-size: 19px;
}

.nav ul {
    list-style: none;
    display: flex;
    justify-content: space-around;
    margin: 0;
    padding: 0;
}

.nav li {
    margin: 0;
}

.nav a {
    color: white;
    text-decoration: none;
    display: block;
    padding: 5px 10px;
}

.nav a:hover {
    color: $secondary-color;
}

.nav a.active {
    color: $secondary-color
}
</style>

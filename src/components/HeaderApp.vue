<template>
    <div class="header">
        <div class="logo">
            <img src="../assets/logo.png" alt="Logo" class="imgLogo">
            <h1><strong class="text-1">Crypto</strong><strong class="text-2">Code</strong></h1>
        </div>
        <div class="dropdown" @click="toggleDropdown">
            <button>{{ userName }}</button>
            <div v-if="showDropdown" class="dropdown-content">
                <a v-if="userName" @click="logout">Cerrar Sesión</a>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import { useRouter } from 'vue-router';
import { useUserStore } from '@/stores/useUserStore';

const userStore = useUserStore();
const userName = computed(() => userStore.userName);
const router = useRouter();

const showDropdown = ref(false);

const toggleDropdown = () => {
    showDropdown.value = !showDropdown.value;
};

const logout = () => {
    userStore.setUserName('');
    localStorage.removeItem('userName');
    router.push({ name: 'HomeView' });
    showDropdown.value = false;
};
</script>

<style scoped lang="scss">

.text-2 {
    color: $primary-color;
}

.text-1 {
    color: $secondary-color;
}

.header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 10px 50px 10px 50px;
}

.logo {
    display: flex;
    align-items: center;
    height: 60px;
}

.imgLogo {
    height: 60px;
    margin-right: 20px;
}

.dropdown {
    position: relative;
    display: inline-block;
    cursor: pointer;
}

.dropdown-content {
    display: none; 
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    background-color: white;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    padding: 12px 16px;
    min-width: 100px;
    z-index: 1;
}

.dropdown-content a {
    text-decoration: none;
    display: block;
    text-align: center;
}

.dropdown:hover .dropdown-content {
    display: block;
}

button {
    padding: 10px 20px;
    min-width: 100px;
    font-size: 16px;
    background-color: $primary-color;
    color: white;
}

button:hover {
    background-color: $secondary-color;
}
</style>
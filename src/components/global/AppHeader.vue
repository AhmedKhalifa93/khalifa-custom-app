<template>
    <div class="header">
        <nav>
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link> |
            <router-link to="/employees">Employee</router-link>
        </nav>
    </div>
</template>

<script>
export default {
    name: "AppHeader",
    setup() {},
};
</script>

<template>
    <div>
        <header class="header">
            <h1>TODO LIST</h1>
            <div id="nav">
                <router-link to="/">Home</router-link> |
                <router-link to="/about">About</router-link>
            </div>
        </header>
        
    </div>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
.header {
    background:grey;
    color: #ffffff;
    text-align: center;
    padding: 10px;
}

.header a {
    color: white;
    padding-right: 5px;
    text-decoration: none;
}
</style>
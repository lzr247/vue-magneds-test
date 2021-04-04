<template>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/collection">Collection</router-link>
    </div>
</template>

<script>
export default {
    name: 'Navigation',
};
</script>

<style lang="scss" scoped>
    #nav {
        padding: 15px;
        text-align: left;
        border-bottom: 1px solid black;
        a {
            font-weight: bold;
            color: #2c3e50;
            &.router-link-exact-active {
            color: #42b983;
            }
        }
    }
</style>
<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  watch: {
    '$store.state.contacts': {
      handler(val) {
        localStorage.setItem('contacts', JSON.stringify(val))
      },
      deep: true
    }
  },
  mounted() {
    this.$store.dispatch('loadContacts')
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


button, input {
  outline: none;
  border-radius: 5px;
  border-width: 1px;
}

button:not([disabled="disabled"]) {
  cursor: pointer;
}

.remove-btn {
  margin-left: 5px;
  font-size: 25px;
  transform: rotate(45deg);
}

.round {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 20px;
  height: 20px;
  border-radius: 50%;
}

a {
  color: #2c3e50;

  &.router-link-exact-active {
    color: #42b983;
  }
}</style>

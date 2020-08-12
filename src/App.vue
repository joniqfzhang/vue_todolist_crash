<template>
  <div id="app">
    <router-view />
  </div>
</template>
<script>
//import Header from './components/layout/Header';
export default {
  components: {
    // Header,
  },
};
</script>

<style>
#nav a {
  font-weight: bold;
  color: #a9adb1;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>

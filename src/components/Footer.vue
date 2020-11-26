<template>
  <div>
    <span>Created by
      <a href="#">Gabriel Dantas</a>
      with
      <a href="#">Vue.js</a>
    </span>
  </div>
</template>

<script>
export default {
  name: 'Footer',
};
</script>

<style scoped>
div {
  width: 100%;
  height: 100%;
  display:flex;
  justify-content: center;
  align-items: center;
}

span, a{
  color: white;
  font-size: .9rem;
  transition: .2s ease-out;
}

a:hover {
  background-color: white;
  color: var(--col-main);
}
</style>

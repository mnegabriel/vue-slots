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
  name: 'TheFooter',
};
</script>

<style scoped>
div {
  width: 100%;
  height: 100%;
  display:flex;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

span, a{
  color: white;
  font-size: .9rem;
  transition: .2s ease-out;
}

a{
  padding: 3px 5px;
  border-radius: 2px;
}

a:hover {
  background-color: white;
  color: var(--col-main);
  transform: translateY(10px);
}
</style>

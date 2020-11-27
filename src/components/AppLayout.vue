<template>
  <div id="layout">
    <header>
      <slot name='header'></slot>
    </header>
    <main>
      <slot></slot>
    </main>
    <footer>
      <slot name='footer'></slot>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'AppLayout',

};
</script>

<style scoped>
#layout {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;

}

header,
footer {
  width: 100%;
  min-height: 50px;
  background-color:var(--col-main);
  display: flex;
  align-items: center;
  justify-content: space-between;
  text-align: center;
}

main {
  flex: 1;
}
</style>

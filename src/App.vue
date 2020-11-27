<template>
  <div id="app">
    <AppLayout>
      <AppUserList>
        <template #title> List of users:</template>
        <template #loading ><TheLoading/></template>
      </AppUserList>
    </AppLayout>
  </div>
</template>

<script>
import AppLayout from '@/components/AppLayout.vue';
import AppUserList from '@/components/AppUserList.vue';
import TheLoading from '@/components/TheLoading.vue';

export default {
  name: 'App',
  components: {
    AppLayout,
    AppUserList,
    TheLoading,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --col-main: rgb(234, 127, 255);
}

html, body, #app, #app > div {
  width:100%;
  min-height: 100vh;
}
</style>

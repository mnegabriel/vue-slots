<template>
  <div id="app">
    <AppLayout >

      <AppUserList>
        <template #userlist="{userlist}">
          <AppUserCardDeck :userlist="userlist"/>
        </template>
        <template #loading ><TheLoading/></template>
      </AppUserList>

      <template #footer><TheFooter/></template>
    </AppLayout>
  </div>
</template>

<script>
import AppLayout from '@/components/Layout/AppLayout.vue';
import TheLoading from '@/components/Layout/TheLoading.vue';
import TheFooter from '@/components/Layout/TheFooter.vue';

import AppUserList from '@/components/Users/AppUserList.vue';
import AppUserCardDeck from '@/components/Users/AppUserCardDeck.vue';

export default {
  name: 'App',
  components: {
    AppLayout,
    TheLoading,
    TheFooter,
    AppUserList,
    AppUserCardDeck,
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

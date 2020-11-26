<template>
  <div id="app">
    <AppLayout>
      <template #header>testando bicha</template>

      <AppButton>
        Oie2
        <IconStar/>
      </AppButton>

      <template #footer><Footer/></template>
    </AppLayout>
  </div>
</template>

<script>
import AppLayout from '@/components/AppLayout.vue';
import AppButton from '@/components/AppButton.vue';
import IconStar from '@/components/IconStar.vue';
import Footer from '@/components/Footer.vue';

export default {
  name: 'App',
  components: {
    AppLayout,
    AppButton,
    IconStar,
    Footer,
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

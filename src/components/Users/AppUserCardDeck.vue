<template>
<ul>
  <li v-for="(user, k) in userlist" :key="k">
    <AppUserCard :user="user"/>
  </li>
</ul>
</template>

<script>
import AppUserCard from '@/components/Users/AppUserCard.vue';

export default {
  name: 'AppUserCardDeck',
  components: {
    AppUserCard,
  },
  props: ['userlist'],
};
</script>

<style>
ul {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(auto-fill,minmax(150px,1fr));
  gap: 30px;
}

</style>

<template>
  <div class="card">
    <section class="image">
      <img
        :src="user.picture.large"
        :alt="user.name.first + ' ' + user.name.last"
      />
    </section>
    <section class="info">
      <h4>{{ user.name.first }}</h4>
    </section>
  </div>
</template>

<script>
export default {
  name: 'AppUserCard',
  props: ['user'],
};
</script>

<style scoped>
.card{
  border-radius: 5px;
  box-shadow: 1px 1px 10px 0 #00000016;
  overflow: hidden;
}

.image img {
  width: 100%;
  object-fit: cover;
}

.info{
  padding: 20px;
}

</style>

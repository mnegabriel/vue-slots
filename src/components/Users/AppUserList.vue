<template>
  <section>
    <slot name='title'>Users</slot>

    <slot name='userlist' :userlist="data.results" v-if="state === 'loaded'">
      <ul class="userlist">
          <li v-for="user in data.results" :key="user.email">

            <slot name='listitem' :user='user'>
              <div>
                <img
                  width="48"
                  height="48"
                  :src="user.picture.large"
                  :alt="user.name.first + ' ' + user.name.last"
                />
                <div>
                  <div>{{ user.name.first }}</div>
                  <slot name="secondrow" :user='user'></slot>
                </div>
              </div>
            </slot>

          </li>
      </ul>
    </slot>

    <slot v-else-if='state==="failed"' name='error'>{{error}}</slot>
    <slot v-else-if="state==='loading'" name='loading'>Loading...</slot>
  </section>
</template>

<script>
const states = {
  idle: 'idle',
  loading: 'loading',
  loaded: 'loaded',
  failed: 'failed',
};
export default {
  data() {
    return {
      state: 'idle',
      data: undefined,
      error: undefined,
      states,
    };
  },
  props: {
    secondrow: {
      type: Function,
      default: () => {},
    },
  },
  mounted() {
    this.load();
  },
  methods: {
    async load() {
      this.state = 'loading';
      this.error = undefined;
      this.data = undefined;
      try {
        const response = await fetch('https://randomuser.me/api/?results=5');
        const json = await response.json();
        this.state = 'loaded';
        this.data = json;
        return response;
      } catch (error) {
        this.state = 'failed';
        this.error = error;
        return error;
      }
    },
  },
};
</script>

<style scoped>
section {
  padding: 20px;
}

.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}

.userlist {
  margin: 10px;
  list-style: none;
}
.userlist img {
  border-radius: 50%;
  margin-right: 1rem;
}
.userlist li + li {
  margin-top: 10px;
}
.userlist li > div {
  display: flex;
  align-items: center;
}
.userlist li div div {
  flex: 1;
}
</style>

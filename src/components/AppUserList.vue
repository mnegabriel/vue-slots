<template>
  <section>
    <slot name='title'>Users</slot>
    <ul class="userlist" v-if="state === 'loaded'">
      <transition-group name="list">
        <li v-for="item in data.results" :key="item.email">
          <div>
            <img
              width="48"
              height="48"
              :src="item.picture.large"
              :alt="item.name.first + ' ' + item.name.last"
            />
            <div>
              <div>{{ item.name.first }}</div>
            </div>
          </div>
        </li>
      </transition-group>
    </ul>
    <slot v-else-if='state==="failed"' name='error'>{{error}}</slot>
    <slot v-else name='loading'>Loading...</slot>
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

<style>
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

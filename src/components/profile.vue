<template>
  <div id="profile" class="centered shadow blur">
    <div class="section vertical">
      <img id="avatar" :src="user.avatar" :alt="user.name"/>
      <p class="title">{{ user.name }} </p>
      <p class="subtitle">A rejoint le {{ user.date }}</p>
    </div>
    <div class="section vertical">
      <div class="badge" v-for="badge in user.badges" :key="badge">
        <img class="icon" :src="badge.icon" :alt="badge.name"/>
        <div class="description">
          <p class="title">{{ badge.name }}</p>
          <p class="subtitle">{{ badge.description }} | {{ badge.date }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'profile',
    props: {
      user: Object
    },
    data() {
      return {}
    },
    methods: {},
    computed: {}
  }
</script>

<style scoped></style>
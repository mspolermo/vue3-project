<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <my-input v-model="post.title" class="input" placeholder="Название"/>
    <my-input v-model="post.body"  class="input" placeholder="Описание"/>
    <my-button
        @click="createPost"
        class="btn"
    >
      Создать
    </my-button>
  </form>
</template>

<script>

export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    },
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
.input {
  margin-top: 15px;
}
.btn {
  margin-top: 15px;
  align-self: flex-end;
}
</style>
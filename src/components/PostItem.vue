<template>
  <div class="post">
    <div>
      <div>{{ post.id }}</div>
      <div>
        <strong>Название: </strong>
        <span>{{ post.title }}</span>
      </div>
      <div>
        <strong>Описание: </strong>
        <span>{{ post.body }}</span>
      </div>
    </div>
    <div class="post__btns">
      <my-button @click="$router.push(`/posts/${post.id}`)">Открыть</my-button>
      <my-button @click="$emit('remove', post)">Удалить</my-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.post {
  margin-top: 15px;
  padding: 15px;
  border: 2px solid teal;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.post__btns {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
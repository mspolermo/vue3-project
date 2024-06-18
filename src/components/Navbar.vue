<template>
  <div class="navbar">
    <div @click="$router.push('/')" >На главную</div>
    <div class="navbar__btns">
      <my-button class="navbar__btn" @click="$router.push('/posts')">Посты</my-button>
      <my-button class="navbar__btn" @click="$router.push('/about')">О сайте</my-button>
      <my-button class="navbar__btn" @click="$router.push('/store')">Store</my-button>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/UI/MyButton.vue";

export default {
  components: {MyButton}

}
</script>

<style scoped>
.navbar {
  height: 50px;
  background: lightgray;
  box-shadow: 2px 2px 4px gray;
  display: flex;
  align-items: center;
  padding: 0 15px;
}
.navbar__btns {
  margin-left: auto;
}
.navbar__btn {
  margin-left: 20px;
}
</style>
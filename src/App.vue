<template>
    <div class="app">
      <h1>Страница с постами</h1>
      <div class="app__btns">
        <my-button @click="showDialog">Создать пост</my-button>
        <my-select v-model="selectedSort" :options="sortOptions" />
      </div>
      <my-dialog v-model:show="dialogVisible">
        <post-form @create="createPost"/>
      </my-dialog>
      <post-list :posts="posts" @remove="removePost" v-if="!isPostLoading"/>
      <div v-else>Загрузка</div>
    </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import axios from "axios";
export default {
  components: {
    PostForm, PostList
  },
    data() {
      return {
        posts: [],
        dialogVisible: false,
        isPostLoading: false,
        selectedSort: '',
        sortOptions: [
          {value: 'title', name: 'По названию'},
          {value: 'body', name: 'По содержимому'}
        ]
      }
    },
    methods: {
      createPost(post) {
        this.posts.push(post);
        this.dialogVisible = false;
      },
      removePost(post) {
        this.posts = this.posts.filter(p => p.id !== post.id)
      },
      showDialog() {
        this.dialogVisible = true;
      },
      async fetchPosts() {
        this.isPostLoading = true;
        try {
            const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
            this.posts = response.data;
        } catch (e) {
          alert('Ошибка получения постов')
        }
        finally {
          this.isPostLoading = false;
        }
      },
    },
    mounted() {
      this.fetchPosts()
    }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
.app__btns {
  margin: 15px 0;
  display: flex;
  justify-content: space-between;
}
</style>
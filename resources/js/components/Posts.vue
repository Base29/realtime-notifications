<template>
  <div class="container">
    <div class="card">
      <post-notify :user="user" :user_notifications="user_notifications" />
    </div>
    <table class="table table-striped">
      <thead class="thead-dark">
        <tr>
          <th scope="col">Title</th>
          <th scope="col">Author</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <template v-for="post in posts" :key="post.id">
          <tr>
            <td>{{ post.title }}</td>
            <td>{{ post.user.name }}</td>
            <td>
              <button
                type="button"
                class="btn btn-sm btn-outline-primary"
                @click="like(post.id)"
              >
                Like
              </button>
            </td>
          </tr>
        </template>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { defineProps, ref, onMounted } from "vue";
import PostNotify from "../components/PostNotify.vue";
const props = defineProps(["posts", "user", "user_notifications"]);

let posts = ref([]);
onMounted(() => {
  posts.value = props.posts;
});
const like = (id) => {
  axios.post("/post-like", { post_id: id }).then((response) => {
    console.log(response.data);
  });
};
</script>
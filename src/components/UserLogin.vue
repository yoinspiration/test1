<template>
  <form @submit.prevent="login">
    <div>
      <input v-model="username" type="text" placeholder="用户名" />
    </div>
    <div>
      <input v-model="password" type="password" placeholder="密码" />
    </div>
    <button type="submit">登录</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.post(
          "https://your-api-url.com/v1/api/loginUser",
          {
            username: this.username,
            password: this.password,
          },
          {
            headers: {
              Authorization: `Bearer -your_token-`,
            },
          }
        );

        console.log(JSON.stringify(response.data, null, 2));
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  margin-bottom: 10px;
}
</style>

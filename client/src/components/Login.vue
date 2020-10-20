<template>
  <div>
    <nav class="navbar navbar-light bg-dark">
      <a class="navbar-brand" href="" style="color: white">
        <img
          src="https://scontent.fphs2-1.fna.fbcdn.net/v/t1.0-9/1002199_194378570740692_1033144520_n.jpg?_nc_cat=102&_nc_sid=85a577&_nc_eui2=AeG1V449y7qBewvqo29YnvtBnFOfCNsigk6cU58I2yKCTkiQhiBO6v2Aw-XqB0jUHlzipERQedc8BQq2pA6ZGCY0&_nc_ohc=QjSOSmEQvXcAX8iEq6p&_nc_ht=scontent.fphs2-1.fna&oh=b8b425db4e399e4e8874073ec589da1c&oe=5FA88520"
          width="30"
          height="30"
          class="d-inline-block align-top"
          alt=""
          loading="lazy"
        />
        ชมรมไอทีแมนมหาวิทยาลัยนเรศวร
      </a>
      <form class="form-inline">
        <a
          href="https://www.facebook.com/weloveitman/"
          class="btn btn-outline-light my-2 my-sm-0"
          type="submit"
        >
          facebook
        </a>
      </form>
    </nav>
    <div class="center">
      <img
        src="https://scontent.fphs2-1.fna.fbcdn.net/v/t1.0-9/119894762_1652719688239899_4158661026406281495_n.jpg?_nc_cat=100&_nc_sid=110474&_nc_eui2=AeErfkjb1vbER6Qfoj1AK0zskfA96pPF82iR8D3qk8XzaMRViUMqnHzcwhibTG0ohz9MEAYlVdmmMuAMWo1iy4mi&_nc_ohc=S8JnB_YKK14AX-V-Ln5&_nc_ht=scontent.fphs2-1.fna&oh=9371af72efa015a489cb884c48b68202&oe=5FA7B427"
        width="70%"
        height="70%"
      />
      <h1>เข้าสู่ระบบ</h1>
      <form v-on:submit.prevent="onLogin">
        <p>
          <input
            class="form-control"
            type="text"
            v-model="email"
            placeholder="Username"
          />
        </p>
        <p>
          <input
            class="form-control"
            type="password"
            v-model="password"
            placeholder="Password"
          />
        </p>
        <p>
          <button
            class="btn btn-primary btn btn-warning"
            style="padding: 3% 36%"
            type="submit"
          >
            เข้าสู่ระบบ
          </button>
        </p>

        <div class="error" v-if="error">{{ error }}</div>
      </form>

    </div>
  </div>
</template>
<script>
import AuthenService from "@/services/AuthenService";
export default {
  data() {
    return {
      email: "",
      password: "",
      error: null,
    };
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    async onLogin() {
      try {
        const response = await AuthenService.login({
          email: this.email,
          password: this.password,
        });
        this.$store.dispatch("setToken", response.data.token);
        this.$store.dispatch("setUser", response.data.user);
        this.$router.push({
          name: "MainAdmin",
        });
      } catch (error) {
        console.log(error);
        this.error = error.response.data.error;
        this.email = "";
        this.password = "";
      }
    },
  },
};
</script>
<style scoped>
.error {
  color: red;
}
.center {
  text-align: center;
  padding: 5% 40%;
}
.op {
  opacity: 0.3;
}
</style>
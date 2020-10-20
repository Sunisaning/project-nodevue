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
        <button v-on:click="logout" class="btn btn-outline-danger">
          ออกจากระบบ
        </button>
      </form>
    </nav>
    <div class="center">
      <h2>ผู้ใช้งานทั้งหมด</h2>
      <h4 class="text-success">
        จํานวนผู้ใช้งาน {{ users.length }} คน

          <button
            class="btn btn-primary"
            v-on:click="navigateTo('/user/create')"
          >
            เพิ่มผู้ดูแล
          </button>

      </h4>
      <div v-for="user in users" v-bind:key="user.id">
        <div class="row">
          <div class="col-sm-12">
            <div class="card">
              <div class="card-body">
                <h5 class="card-title">รหัสผู้ใช้งาน : {{ user.id }}</h5>
                <p>ชื่อ-นามสกุล : {{ user.name }} - {{ user.lastname }}</p>
                <p>อีเมล : {{ user.email }}</p>
                <p>รหัสผ่าน : {{ user.password }}</p>
                <p>สถานะ : {{ user.status }}</p>
                <button
                  class="btn btn-primary btn-warning"
                  v-on:click="navigateTo('/user/edit/' + user.id)"
                >
                  แก้ไขข้อมูล
                </button>
                <button
                  class="btn btn-primary btn-warning"
                  v-on:click="deleteUser(user)"
                >
                  ลบข้อมูล
                </button>
              </div>
            </div>
          </div>
        </div>
        <br />
      </div>
    </div>
  </div>
</template>
<script>
import UsersService from "@/services/UsersService";

export default {
  data() {
    return {
      users: [],
    };
  },
  async created() {
    this.users = (await UsersService.index()).data;
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    async deleteUser(user) {
      let result = confirm("Want to delete?");
      if (result) {
        try {
          await UsersService.delete(user);
          this.refreshData();
        } catch (err) {
          console.log(err);
        }
      }
    },
    async refreshData() {
      this.users = (await UsersService.index()).data;
    },
    logout() {
      this.$store.dispatch("setToken", null);
      this.$store.dispatch("setUser", null);
      this.$router.push({
        name: "login",
      });
    },
  },
};
</script>
<style scoped>
.center {
  text-align: center;
  padding: 3% 20%;
}
</style>
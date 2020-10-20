<template>
  <div class="bg-light">
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
        <button v-on:click="logout" class="btn btn-outline-danger">ออกจากระบบ</button>
      </form>
    </nav>
    <div class="center">
      <h1>ยินดีต้อนรับเข้าสู่ระบบ!!</h1>
      <br />
      <div class="row">
        <div class="col-sm-6">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">การนัดหมายใช้บริการลงระบบปฏิบัติการ Windows</h5>
              <p class="card-text">
                Appointment for serviceinstall Windows .
              </p>
              <button class="btn btn-primary btn-warning" v-on:click="navigateTo('/windows')">
                ดูทั้งหมด
              </button>
            </div>
          </div>
        </div>
        <div class="col-sm-6">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">การนัดหมายให้คำปรึกษา</h5>
              <p class="card-text">
                Appointment for a computer problem consultation .
              </p>
              <button class="btn btn-primary btn-warning" v-on:click="navigateTo('/advices')">
                ดูทั้งหมด
              </button>
            </div>
          </div>
        </div>
      </div>
      <br />
      <div class="row">
        <div class="col-sm-12">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">ผู้ใช้งานทั้งหมด</h5>
              <p class="card-text">
                Total admins in this system.
              </p>
              <button class="btn btn-primary btn-warning" v-on:click="navigateTo('/users')">
                ดูทั้งหมด
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    navigateTo(route) {
      this.$router.push(route);
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
  padding: 5%;
}
</style>
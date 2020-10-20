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
      <h2>การนัดให้คำปรึกษาทั้งหมด</h2>
      <h4 class="text-success">จํานวนการนัด {{ advices.length }} คิว</h4>
      <div v-for="advice in advices" v-bind:key="advice.id">
        <div class="row">
          <div class="col-sm-12">
            <div class="card bg-light">
              <div class="card-body">
                <h5 class="card-title">รหัสการนัดหมาย : {{ advice.id }}</h5>
                <p>ชื่อ-นามสกุล : {{ advice.name }} - {{ advice.lastname }}</p>
                <p>เบอร์โทร : {{ advice.tel }}</p>
                <p>วันที่นัดหมาย : {{ advice.date }}</p>
                <button class="btn btn-primary btn-warning" v-on:click="navigateTo('/advice/edit/' + advice.id)">
                  แก้ไขข้อมูล
                </button>
                <button class="btn btn-primary btn-warning" v-on:click="deleteAdvice(advice)">ลบข้อมูล</button>
              </div>
            </div>
          </div>
        </div>
        <br>
      </div>
    </div>
  </div>
</template>
<script>
import AdviceService from "@/services/AdviceService";

export default {
  data() {
    return {
      advices: [],
    };
  },
  async created() {
    this.advices = (await AdviceService.index()).data;
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
    async deleteAdvice(advice) {
      let result = confirm("ต้องการลบใช่ไหม ?");
      if (result) {
        try {
          await AdviceService.delete(advice);
          this.refreshData();
        } catch (err) {
          console.log(err);
        }
      }
    },
    async refreshData() {
      this.advices = (await AdviceService.index()).data;
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
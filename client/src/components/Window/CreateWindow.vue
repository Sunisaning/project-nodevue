<template>
  <div class="bg-light">
    <div class="center">
      <h1>นัดใช้บริการติดตั้งระบบปฏิบัติการ Windows</h1>
      <div class="row">
        <div class="col-sm-12">
          <div class="card">
            <div class="card-body">
              <form v-on:submit.prevent="createWindow">
                <p class="left">
                  ชื่อ:
                  <input
                    class="form-control"
                    type="text"
                    v-model="window.name"
                  />
                </p>
                <p class="left">
                  นามสกุล:
                  <input
                    class="form-control"
                    type="text"
                    v-model="window.lastname"
                  />
                </p>
                <p class="left">
                  เบอร์โทร:
                  <input
                    class="form-control"
                    type="text"
                    v-model="window.tel"
                  />
                </p>
                <p class="left">
                  จำนวนเครื่อง:
                  <input
                    class="form-control"
                    type="text"
                    v-model="window.quantity"
                  />
                </p>
                <p class="left">
                  วันที่นัดใช้บริการ:
                  <input
                    class="form-control"
                    type="date"
                    v-model="window.date"
                  />
                </p>
                <p>
                  <button class="btn btn-primary btn-warning" type="submit">
                    นัดหมาย
                  </button>
                </p>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import WindowService from "@/services/WindowService";
export default {
  data() {
    return {
      window: {
        name: "",
        lastname: "",
        tel: "",
        quantity: "",
        date: "",
      },
    };
  },
  methods: {
    async createWindow() {
      try {
        await WindowService.post(this.window);
        this.$router.push({
          name: "MainUser",
        });
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>
<style scoped>
.center {
  text-align: center;
  padding: 3% 20%;
}
.left {
  text-align: left;
}
</style>
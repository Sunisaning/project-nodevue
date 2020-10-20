<template>
  <div >
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
        width="30%"
        height="30%"
      />
      <h1>ยินดีต้อนรับเข้าสู่!!</h1>
      <h1>ชมรมไอทีแมนมหาวิทยาลัยนเรศวร</h1>
      <div class="jumbotron">
        <h1 class="display-4">บริการให้ปรึกษาปัญหาคอมพิวเตอร์</h1>
        <p class="lead">
          เมื่อทำการนัดหมายสำเร็จแล้ว สามารถเข้าปรึกษาปัญหาคอมพิวเตอร์ได้ที่ ตึก Citcoms ชั้น 6 
          เวลา 17.00 - 19.00 น. ในวันที่ทำการนัดหมายไว้
        </p>
        <hr class="my-4" />
        <button
          class="btn btn-primary btn-warning"
          v-on:click="navigateTo('/advice/create')"
          role="button"
        >
          สร้างการนัดหมาย
        </button>
      </div>
      <div class="jumbotron">
        <h1 class="display-4">บริการติดตั้งระบบปฏิบัติการ Windows</h1>
        <p class="lead">
          เมื่อทำการนัดหมายสำเร็จแล้ว ให้นำคอมพิวเตอร์ของตนเองมาที่ ตึก Citcoms ชั้น 6 
          เวลา 17.00 - 19.00 น. ในวันที่ทำการนัดหมายไว้
        </p>
        <hr class="my-4" />
        <button
          class="btn btn-primary btn-warning"
          v-on:click="navigateTo('/window/create')"
          role="button"
        >
          สร้างการนัดหมาย
        </button>
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
  },
};
</script>

<style>
.center {
  text-align: center;
  padding: 5%;
}
</style>
<template>
  <div>
    <h1>Watch</h1>
    <p>ID: {{ userId }}</p>
    <p>ยี่ห้อ {{ user.name }} - {{ user.lastname }}</p>
    <p>รุ่นนาฬิกา: {{ user.email }}</p>
    <p>ราคา: {{ user.password }}</p>
  </div>
</template>
<script>
import UserService from "@/services/UsersService";
export default {
  data() {
    return {
      user: null,
    };
  },
  async created() {
    try {
      let userId = this.$route.params.userId;
      this.user = (await UserService.show(userId)).data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
</style>
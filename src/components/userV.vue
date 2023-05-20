<template>
  <div>
    <table>
      <tr>
        <td>姓名</td>
        <td>性别</td>
        <td>生日</td>
        <td>地址</td>
      </tr>
      <td>{{users.name}}</td>
      <td>{{users.sex}}</td>
      <td>{{users.birth}}</td>
      <td>{{users.birthaddr}}</td>
    </table>
  </div>
</template>

<script>
export default {
  name: "userV",
  data(){
    console.log('进入userV页面')
    return {
      users:[]
    }
  },
  created() {
    console.log('userV页面获取数据')
    var that=this;
    this.$axios.get('http://localhost:8080/user/show').then(function (resp) {
      that.users=resp.data;
      that.users.name=resp.data[0].name;
      that.users.sex=resp.data[0].sex;
      that.users.birth=resp.data[0].birth;
      that.users.birthaddr=resp.data[0].birthaddr;
    })
  },
}
</script>

<style scoped>

</style>

<template>
       <el-card class="box-card">
  <div slot="header" class="clearfix">
    <span><font size="2">Android本地商城</font></span>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getusers">源码下载</el-button>
  </div>
  <div class="text item">
    <font size="2">Android本地商城功能设计</font>
      <p>1、角色，功能设计</p>
      <p>拥有管理员（root）、一个卖家、若干买家。三方需要实现的具体功能如下：</p>
      <p>1.1、root（一个）初始登陆用户名：root 密码：123456</p>
      <p>添加/删除用户、配置用户角色类型、角色类型的权限控制</p>
      <p>1.2、卖家（一个）</p>
      <p>设置销售产品信息、不同商品的信息、处理用户订单（发货）</p>
      <p>1.3、买家（若干）</p>
      <p>用户登录、配置用户属性信息、浏览商品目录、显示商品详情、搜索商品、购买商品、结账、下订单、订单查看</p>
      <font color="#5CACEE" @click="getwiki">1.4、其他设计详情查看wiki</font>

  </div>
</el-card>
</template>

<script>
export default {
  name: 'dataTables',
  data () {
    return {
      multipleSelection: [],
      url:"https://gitee.com/xiaolanyun/XiaoLanYunMart"//Android本地商城
    }
  },
  methods: {
    toggleSelection (rows) {
      if (rows) {
        rows.forEach(row => {
          this.$refs.multipleTable.toggleRowSelection(row);
        });
      } else {
        this.$refs.multipleTable.clearSelection();
      }
    },
    handleSelectionChange (val) {
      this.multipleSelection = val;
    },
      getusers(){
      window.setTimeout("window.open('https://gitee.com/xiaolanyun/XiaoLanYunMart')", 1000);
    },
    getwiki(){
      window.setTimeout("window.open('https://xiaolanyun.github.io/DevOps_wiki/chapter10.html')",1000);
    }
  }
}
</script>

<style scoped>
  h3{
    margin: 25px 0 20px;
    font-weight: 400;
    color: #1f2f3d;
    font-size: 22px;
  }
  p{
    font-size: 14px;
    color: #5e6d82;
    line-height: 1.5em;
  }
</style>

<template>
       <iframe :src="url" width="100%" height="1000px"></iframe>
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

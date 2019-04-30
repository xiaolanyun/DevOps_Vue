<template>
       <el-card class="box-card">
  <div slot="header" class="clearfix">
    <span><font size="2">接口自动化测试示例</font></span>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getusers">示例下载</el-button>
  </div>
  <div class="text item">
        <font size="2">1、接口测试设计思路</font>
        <p><img v-bind:Src="imgSrc1" height="362" width="988px"/></p>
        <!-- <p><br></p>
        <font size="2">2、newman执行脚本并生成报告</font>
        <p>输入newman查看可使用命令参数。</p>
        <p>可生成测试报告类型：json,junit的xml，html.</p>
        <pre><code>newman run phonecheck.json
    –reporterscli,html,json,junit --reporter-json-export poptestjsonOut.json
    --reporter-junit-export poptestxmlOut.xml --reporter-html-export poptesthtmlOut.html
    </code></pre>
        <br>
        <font size="2">3、newmanApiTest_shell.sh</font>
        <pre><code>#!/bin/sh -l
        source /etc/profile
        cnpm install
        echo 正在进行接口自动化........
        newman run phonecheck.json -reporterscli,html,json --reporter-json-export poptestjsonOut.json --reporter-html-export poptesthtmlOut.html
        echo 报告已经生成，正在打包......
        tar -zcvf ${BUILD_NUMBER}_${JOB_NAME}_report.tar.gz ./newman
        echo 请您查看邮件或者jenkins构建日志输出台！
        </code></pre> -->
  </div>
</el-card>
</template>

<script>
export default {
  name: 'dataTables',
  data () {
    return {
      multipleSelection: [],
      url:"https://gitee.com/xiaolanyun/DevOps_ApiTest",//手机号码api测试
      imgSrc1:"./static/images/接口测试思路.PNG",
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
      window.setTimeout("window.open('https://gitee.com/xiaolanyun/DevOps_ApiTest')", 1000);
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

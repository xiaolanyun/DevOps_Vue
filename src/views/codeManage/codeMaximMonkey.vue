<template>
       <el-card class="box-card">
  <div slot="header" class="clearfix">
    <span><font size="2">Maxim_Monkey框架</font></span>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getmp4">运行展示</el-button>
    <br>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getusers">框架下载</el-button>
  </div>
  <div class="text item">
      <font size="2">1、设计思路</font>
      <p><img v-bind:Src="imgSrc1" height="382" width="1206px"/></p>
      <!-- <pre><code>
      adb push framework.jar /sdcard/01test

      adb push monkey.jar /sdcard/01test

      adb push max.config /sdcard/01test
      </code></pre><p>普通测试：</p>
      <pre><code>adb shell CLASSPATH=/sdcard/01test/monkey.jar:/sdcard/01test/framework.jar exec app_process /system/bin tv.panda.test.monkey.Monkey -p
      com.example.xiaolanyun.ldmart --uiautomatormix --running-minutes 1 -v -v
      </code></pre><p>增加截图功能：</p>
      <pre><code>截图及dump xml
      配置
      Max.config 
      max.takeScreenShot= true   开启截图

      max.savePageSource  保存xml
      </code></pre><p>截图的生效条件：</p>
      <p>throttle &gt; 200  &amp;&amp;  max.takeScreenShot= true</p>
      <p>带截图测试：</p>
      <pre><code>adb shell CLASSPATH=/sdcard/01test/monkey.jar:/sdcard/01test/framework.jar exec app_process /system/bin tv.panda.test.monkey.Monkey -p 
        com.example.xiaolanyun.ldmart --uiautomatormix --running-minutes 2 -v -v --throttle 400 --output-directory /sdcard/01test/screenshot
      </code></pre>
      <font size="2">2、模式选择</font>
      <p>1、模式 DFS
        --uiautomatordfs</p>
      <p>  增加深度遍历算法</p>
      
      <p>2、 模式 Mix </p>
      <p>--uiautomatormix</p>
      <p>直接使用底层accessibiltyserver获取界面接口 解析各控件，随机选取一个控件执行touch操作。</p>
      <p>  同时与原monkey 其他操作按比例混合使用</p>
      <p>  默认accessibilityserver action占比50%，其余各action分剩余的50%</p>
      <p>  accessibilityserver action占比可配置 --pct-uiautomatormix n</p>
      
      <p>3、模式Troy</p>
      <p>  --uiautomatortroy</p>
      <p>  控件选择策略按max.xpath.selector配置的高低优先级来进行深度遍历</p>
      <br>
      <font size="2">3、jenkins脚本配置的monkey_shell.sh</font>
            <pre><code>#!/bin/bash
      source /etc/profile
      echo 正在创建截图保存文件夹
      mkdir ./${BUILD_NUMBER}_${JOB_NAME}_result
      echo 正在执行Maim_monkey
      adb push framework.jar monkey.jar max.config /sdcard/01test
      adb shell CLASSPATH=/sdcard/01test/monkey.jar:/sdcard/01test/framework.jar exec app_process /system/bin tv.panda.test.monkey.Monkey -p com.example.xiaolanyun.ldmart --uiautomatormix --running-minutes 2 -v -v --throttle 400 --output-directory /sdcard/01test/${BUILD_NUMBER}_${JOB_NAME}_screenshot
      echo 执行完毕，正在将截图保存
      adb pull /sdcard/01test/${BUILD_NUMBER}_${JOB_NAME}_screenshot ./${BUILD_NUMBER}_${JOB_NAME}_result
      echo 正在打包截图
      tar -zcvf ${BUILD_NUMBER}_${JOB_NAME}_screenshot.tar.gz ./${BUILD_NUMBER}_${JOB_NAME}_result
      echo 打包已经完成，请您配合日志查看！
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
      url:"https://gitee.com/xiaolanyun/DevOps_Monkey",//monkey
      imgSrc1:"./static/images/Maxim_monkey设计思路.PNG",
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
      window.setTimeout("window.open('https://gitee.com/xiaolanyun/DevOps_Monkey')", 1000);
    },
    getmp4(){
      window.setTimeout("window.open('https://www.bilibili.com/video/av50838305/?p=7')",1000);
      window.setTimeout("window.open('https://www.bilibili.com/video/av50838305/?p=6')",1000);
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

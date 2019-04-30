<template>
  <el-card class="box-card">
  <div slot="header" class="clearfix">
    <span><font size="2">并行测试框架</font></span>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getmp4">运行展示</el-button>
    <br>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getusers">框架下载</el-button>
    
  </div>
  <div class="text item">
      <font size="2">1、设计思路</font>
      <p><img v-bind:Src="imgSrc1" height="503" width="1217px"></p>
      <!-- <p>对Appium测试框架进一步改进，使其实现并行测试，由于物理机资源有限，暂时只进行两台安卓设备并行测试。</p>
      <p>对SelectDriver.java进行修改，增加设备udid的获取与自动设置。</p>
      <p>以selenium-server-standalone为支撑，由selenium-grid分配测试。</p>
      <p>利用testng进行xml传参，设置测试用例执行机的udid，实现并行测试。</p>
    -->
      <br>
      <font size="2">2、工程讲解</font>
      <p><img v-bind:Src="imgSrc2" height="862" width="808px"/></p>
      <!-- <p>运行顺序Grid-》appiumA,appiumB</p>
      <p><img v-bind:src="imgSrc1" alt=""></p>
      <font size="2">2.1、启动AppiumGrid服务</font>
      <pre><code>@echo off

      echo 正在启动Appium grid服务，请稍等。

      echo 启动完毕之后，请不要关闭此窗口。

      echo 当你看到"Selenium Grid hub is up and running"则表示启动成功。

      java -jar selenium-server-standalone-2.53.0.jar -role hub -port 4444
      </code></pre>
      <font size="2">2.2、启动AppiumServer[A]</font>
      <pre><code>@echo off

      echo 启动appium server中，请不要关闭此窗口。

      appium -a 127.0.0.1 -p 4723 -bp 4724   --selendroid-port 8090 --chrom edriver-port 9515 --session-override --nodeconfig nodeconfig_1.json
      </code></pre>
      <font size="2">2.3、启动AppiumServer[B]</font>
      <pre><code>@echo off

      echo 启动appium server中，请不要关闭此窗口。

      appium -a 127.0.0.1 -p 4725 -bp 4726   --selendroid-port 8091 --chromedriver-port 9516 --session-override --nodeconfig nodeconfig_2.json
      </code></pre>
      <font size="2">2.4、nodeconfig_1.json</font>
      <pre><code>{
          "capabilities":
          [
              {
              "browserName": "zuk",
              "version":"6.0.1",
              "maxInstances": 1,
              "platform":"WINDOWS"
              }
          ],
          "configuration":
          {
              "cleanUpCycle":2000,
              "timeout":30000,
              "proxy": "org.openqa.grid.selenium.proxy.DefaultRemoteProxy",
              "url":"http://127.0.0.1:4723/wd/hub",
              "host": "127.0.0.1",
              "port": 4723,
              "maxSession": 1,
              "register": true,
              "registerCycle": 5000,
              "hubPort": 4444,
              "hubHost": "127.0.0.1"
          }
      }
      </code></pre>
      <font size="2">2.5、nodeconfig_2.json</font>
      <pre><code>{
          "capabilities":
          [
              {
              "browserName": "redmi",
              "version":"6.0.1",
              "maxInstances": 1,
              "platform":"WINDOWS"
              }
          ],
          "configuration":
          {
              "cleanUpCycle":2000,
              "timeout":30000,
              "proxy": "org.openqa.grid.selenium.proxy.DefaultRemoteProxy",
              "url":"http://127.0.0.1:4725/wd/hub",
              "host": "127.0.0.1",
              "port": 4725,
              "maxSession": 1,
              "register": true,
              "registerCycle": 5000,
              "hubPort": 4444,
              "hubHost": "127.0.0.1"
          }
      }
      </code></pre>
      <br>
      <font size="2">3、linux下shell脚本编写</font>
      <p>其中nodeconfig_1.json和nodeconfig_2.json内容不变</p>
      <p><img v-bind:src="imgSrc2" alt=""></p>
      <font size="2">3.1、appiumServiceA.sh</font>
      <pre><code>*#!/bin/bash*

      echo 启动appium server中，请不要关闭此窗口。

      ./appium-desktop-1.10.0-x86_64.AppImage -a 127.0.0.1 -p 4723 -bp 4724   --selendroid-port 8090 --chrom edriver-port 9515 --session-override 
      --nodeconfig nodeconfig_1.json
      </code></pre>
      <font size="2">3.2、appiumServiceB.sh</font>
      <pre><code>*#!/bin/bash*

      echo 启动appium server中，请不要关闭此窗口。

      ./appium-desktop-1.10.0-x86_64.AppImage -a 127.0.0.1 -p 4725 -bp 4726   --selendroid-port 8091 --chromedriver-port 9516 --session-override 
      --nodeconfig nodeconfig_2.json
      </code></pre>
      <font size="2">3.3、gridService.sh</font>
      <pre><code>*#!/bin/bash*

      echo 正在启动Appium grid服务，请稍等。

      echo 启动完毕之后，请不要关闭此窗口。

      echo 当你看到"Selenium Grid hub is up and running"则表示启动成功。

      java -jar selenium-server-standalone-2.53.0.jar -role hub -port 4444
      </code></pre>
      <font size="2">3.4、shuoming.txt，方便复制开启服务</font>
      <pre><code>./gridService.sh
      ./appiumServiceA.sh
      ./appiumServiceB.sh
      </code></pre>
      <br>
      <font size="2">4、快速上手</font>

      <p><br></p>

      <font size="2">4.1、开启服务配置</font>
      
      <p>由于windos和centos都安装的是桌面版appium，所以配置参数部分都在appium中配置，即配置脚本中4723和4725两个appium服务，并设置，</p>
      <p><img v-bind:src="imgSrc3" alt="" width="1000px"></p>
      <p>图中直接设置了node配置为nodeconfig_1.json和nodeconfig_2.json是因为通过脚本打开时Appium面板时自动读取到脚本中nodeconfig设置，故不需配置路径。</p>
      <p>运行时，先启动Grid脚本，再启动appiumA,appiumB两个脚本，然后会自动打开桌面版appium两个窗口，选择保存好的4723和4725两个appium服务依次启动。<strong>必须是脚本启动面板，点击运行两个Appium服务才可以</strong></p>
      <p>即可进行测试。</p>
      <p>说明：设备名称在nodeconfig_1.json和nodeconfig_2.json中配置</p>
      <pre><code>"browserName": "zuk",

      "browserName": "redmi"
      </code></pre>
      <p>设备udid获取</p>
      <pre><code>adb devices
      </code></pre><p>设备的udid在testng.xml中需要运行的测试用例下配置，如</p>
      <pre><code>&lt;test name="管理员界面切换" preserve-order="true"&gt;
              &lt;parameter name="udid" value="113a20777d33"/&gt; 
              &lt;parameter name="deviceName" value="redmi"/&gt;
              &lt;packages&gt;
                  &lt;package name="com.xiaolanyun.appium.DataTest.testCase.RootNavigation" /&gt;
              &lt;/packages&gt;
          &lt;/test&gt;
          &lt;test name="管理员登陆添加买家卖家账户并购买商品发货" preserve-order="true"&gt;
              &lt;parameter name="udid" value="63a7b810"/&gt;
              &lt;parameter name="deviceName" value="zuk"/&gt;
              &lt;packages&gt;
                  &lt;package name="com.xiaolanyun.appium.DataTest.testCase.RootAddUserAndBuyGoods" /&gt;
              &lt;/packages&gt;
          &lt;/test&gt;
      </code></pre>
      <font size="2">4.2、测试用例编写顺序，格式参照Appium测试框架。</font><br>
      <font size="2">4.3、增加测试设备</font>
      <p>按照格式相应的增加nodeconfig配置文件，按照格式编写Appium启动脚本，增加Appium面版服务配置，进行testng.xml中的测试用例设备udid分配。</p>
      <font size="2">4.4、本地运行</font>
        <p>在相应testng.xml上右键，run as->TestNG suit</p>
      
      <br>
      <font size="2">5、好处</font>
      <p>多机器并行测试提高测试效率</p>-->
  </div> 
</el-card>
</template>

<script>
export default {
  name: 'dataTables',
  data () {
    return {
      multipleSelection: [],
      url:"https://gitee.com/xiaolanyun/DevOps_AppiumParallelTest",//Appium多机器并行测试框架
      imgSrc1:'./static/images/并行测试框架思路.PNG',
      imgSrc2:'./static/images/DevOps_AppiumParallelTest.PNG',
      // imgSrc3:'./static/images/11.5.2.PNG'
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
      window.setTimeout("window.open('https://gitee.com/xiaolanyun/DevOps_AppiumParallelTest')", 1000);
    },
    getmp4(){
      window.setTimeout("window.open('https://www.bilibili.com/video/av50838305/?p=3')",1000);
      window.setTimeout("window.open('https://www.bilibili.com/video/av50838305/?p=4')",1000);
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

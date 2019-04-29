<template>
<el-card class="box-card">
  <div slot="header" class="clearfix">
    <span><font size="2">Appium自动化测试框架</font></span>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getmp4">视频展示</el-button>
    <br>
    <el-button style="float: right; padding: 3px 0" type="text" @click="getuser">框架下载</el-button>
    
  </div>
  <font size="2">1、Appium图解</font>
  <p><img v-bind:Src="imgSrc1" height="300" width="700px"/></p>
  <br>
  <font size="2">2、设计思路</font>
  <p><img v-bind:Src="imgSrc2" height="400" width="700px"/></p>
  <br>
  <font size="2">3、框架展示</font>
  <p><img v-bind:Src="imgSrc3" height="1200" width="500px"/></p>
  <br>
  <div class="text item">

      <font size="2">4、包类文件类解释：</font>
      <p><strong>base包：</strong></p>
      <p>BasePerpare.java：启动和结束测试，以及数据提供者，提供测试数据,预处理</p>
      <p><strong>pages包：</strong>页面元素存放</p>
      <p><strong>pagesHelper包：</strong></p>
      <p>对该页面的操作方法存放，如点击，等待加载，验证文本内容，输入，清空等方法</p>
      <p><strong>plugins包：</strong></p>
      <p>excel和html插件</p>
      <p><strong>testCase包：</strong></p>
      <p>测试用例，调用Helper里面的各种方法进行操作</p>
      <p><strong>utils包：</strong></p>
      <p><strong>AppiumUtil.java:</strong></p>
      <p>封装appium的api:</p>
      <p>1、获取driver；</p>
      <p>2、退出app；</p>
      <p>3、退出移动浏览器；</p>
      <p>4、通过By对象去查找某个元素；</p>
      <p>5、通过By对象去查找一组元素；</p>
      <p>6、清空元素内容；</p>
      <p>7、输入内容；</p>
      <p>8、点击；</p>
      <p>9、查找一个元素，appium新增的查找元素方法；</p>
      <p>10、查找一组元素，appium新增的查找元素方法；</p>
      <p>11、获取文本1{getText(By by)}；</p>
      <p>12、获取文本2{getText(String locateWay,String locateValue)}；</p>
      <p>13、提交；</p>
      <p>14、获得webview页面的标题；</p>
      <p>15、获得元素属性的文本；</p>
      <p>16、在给定的时间内找元素，如果没有找到则超时，抛出异常；</p>
      <p>17、判断文本是不是和需求要求的文本一致；</p>
      <p>18、暂停当前用力地执行，暂停的是件为：sleepTime；</p>
      <p>19、根据元素来获取次元素的定位值；</p>
      <p>20、判断实际文本时候包含期望文本；</p>
      <p>21、跳转到webview页面（int index）；</p>
      <p>22、跳转到webview页面（String contextName）;</p>
      <p>23、执行javascript方法；</p>
      <p>24、执行JavaScript方法和对象；</p>
      <p>25、检查元素是不是存在；</p>
      <p>26、长按操作；</p>
      <p>27、滑动；</p>
      <p>28、滚动，根据文本模糊匹配；</p>
      <p>29、滚动，根据文本精准匹配；</p>
      <p>30、拖拽操作；</p>
      <p>31、 放大和缩小；</p>
      <p>32、app置于后台运行；</p>
      <p>33、收起键盘；</p>
      <p>34、安装app；</p>
      <p>35、app是否安装；</p>
      <p>36、页面过长时候滑动页面window.scrollTo(左边距，上边距)；</p>
      <p>37、后退</p>
      <p>38、打开应用</p>
      <p><strong>LogConfiguration.java:</strong></p>
      <p>配置日志</p>
      <p><strong>PropertiesDataProvide.java:</strong></p>
      <p>从.properties文件中读取相关测试数据<br></p>
      <p><strong>SelectDriver.java:</strong></p>
      <p>根据测试平台的不同生成不同的driver 比如AndroidDriver 或者是IOSDriver</p>
      <p><strong>result文件夹：</strong></p>
      <p>存放结果，包括excel和html结果</p>
      <p><strong>xml文件：</strong></p>
      <p>default.xml【书上自己建立的一个testng默认配置文件，要有】和testng.xml【这个是我自己生成的一个默认配置，不用管，没有也可以】</p>
      <p>runAll.xml:测试多条用例顺序执行测试</p>
      <p>runSingle.xml:测试单条用例执行测试</p>
      <p>runSmoke.xml:冒烟测试</p>
      <p>pom.xml:maven仓库管理依赖配置文件,以及要运行的testng.xml测试用例文件</p>
      <p>【详细解释</p>
      <p><strong>Base</strong></p>
      <p>BasePrepare.java,这个类的主要作用是启动和关闭APP的作用，启动APP使用了TetsNG的@BeforeClass ，在@BeforeClass下会初始化APP并设置与APPIUM通信的相关数据。关闭APP使用了TestNG的@AfterClass，在这个注释下写了APP退出的操作；测试用例类中则是以@Test注释为主体的，在@Test注释下，书写了完整的测试步骤。测试用例继承这个BasePrepare.java</p>
      <p><strong>pages</strong></p>
      <p>页面元素类，每一个java类，都是一个页面，存放的都是对应页面的所有元素</p>
      <p><strong>pageshelper</strong></p>
      <p>存放的是对应页面的帮助类，这是什么意思？简单的说：在这个页面上做了什么操作都写在这个pageshelper中，如登录页面的方法</p>
      <p><strong>plugins</strong></p>
      <p>主要存放的是html报告插件和excel报告插件</p>
      <p><strong>Testcases</strong></p>
      <p>存放测试用例，有很多子包，子包的个数根据你测试的系统的模块来划分</p>
      <p><strong>Utils</strong></p>
      <p>封装了各种工具类，包括读取excel，appium api封装类，读取数据库类，读取属性文件类和生成driver的类等。</p>
      <p><strong>其余文件说明，不一定要自己去建立</strong></p>
      <p><strong>bin目录：</strong></p>
      <p>项目编译生成class文件存放目录，这个目录不用去管，Eclipse会自动控制。</p>
      <p><strong>config目录：</strong></p>
      <p>存储框架类所需的所有属性文件，比如arrow的配置文件以及自定义的一些属性文件。</p>
      <p><strong>result目录：</strong></p>
      <p>存储测试框架运行测试用例生成的报告（包含log，截图等）</p>
      <p><strong>src和target目录：</strong></p>
      <p>可以不用管，由maven控制即可，整个框架，没有用到此目录，大家可以忽略。</p>
      <p>接下来还剩几个xml文件，我们也来一一介绍一下：</p>
      <p><strong>pom.xml：</strong></p>
      <p>maven的配置文件，项目核心配置，用于构建项目、自动下载项目依赖以及后续的和testng、jenkins配合持续集成等</p>
      <p><strong>runAll.xml：</strong></p>
      <p>这是testng的配置文件，用于存放部分测试数据以及测试的平台，浏览器的配置、加入第三方插件监听（arrow插件）、设置用例执行策略（多线程还是单线程，顺序执行还是无序执行以及是否依赖执行等）以及设置要执行的用例。之所以改成runAll顾名思义就是说执行整个web项目的所有模块的用例的测试</p>
      <p><strong>runSingle.xml</strong></p>
      <p>和runAll.xml一样，不多解释，不一样的地方就是用它来做单个用例的调试改错，只涉及到单个的类（用例），所以调试改错专用。比如我用runAll.xml跑完了所有的用例，但是发现个别用例失败，此时先去分析log，如果是代码问题就去调试代码，调试完毕之后就去用runSingle.xml去跑一边此用例。</p>
      <p><strong>default.xml:</strong> </p>
      <p>只存储了测试参数（parameter）以及监听器（arrow），没有任何测试用例放在里面，这个xml文件是为了本框架的一个默认testng配置文件，主要是为了，直接在测试用例中右键运行测试用例，如果不配置一个默认的文件，直接在测试用例类中直接运行会跳过用例。因为xml文件中存储了一些必须的参数，比如测试浏览器是什么，测试平台是什么等等。框架搭建过程中会讲到如何设置default.xml文件。</p>
      <p><strong>runSmoke.xml：</strong></p>
      <p>这个主要执行冒烟测试用的，冒烟测试我们会先一些基本和核心功能作为测试重点，迅速跑一遍这些功能点，看看这个软件版本能不能released</p>
      <p>】</p>
      <br>
      <font size="2">5、框架快速上手</font>
      <p>本地编写测试用例，首先需要配置好环境。</p>
      <p>1、编写示例：以登陆界面为例</p>
      <p>pages包下建立LoginPage.java，定义界面元素，格式参见框架源码相应文件。</p>
    
      <p>pagesHelper包下建立LoginPageHelper.java,封装对登陆界面元素操作的方法，其操作函数调用的是Utils包下封装的appium函数，格式参见框架源码相应文件。</p>
    
      <p>testCase包下建Login包，Login包下建立LoginPage_001_UICheckForLogin_Test.java，是测试用例，调用pagesHelper包下的LoginPageHelper.java中封装的操作方法，编写测试逻辑，格式参见框架源码相应文件。</p>
      <p>命名规范：</p>
      <p style="text-indent:4em;">1、操作页面，LoginPage，必须带有Page字段</p>
      <p style="text-indent:4em;">2、用例编号，001，输出测试报告时进行读取，必须设置</p>
      <p style="text-indent:4em;">3、测试用例描述，UICheckForLogin</p>
      <p style="text-indent:4em;">4、文件作用，Test</p>
  
      <p>2、在testng.xml中配置appium和手机相关参数，配置需要运行的测试用例，格式参见源码相应文件。</p>
      
      <p>3、在pom.xml中配置需要运行的testng.xml文件，jenkins定时测试需要读取。格式参见框架源码相应文件。</p>
      <p>4、本地运行：在相应testng.xml上右键，run as->TestNG suit</p>
     
      <br>
      <font size="2">6、好处</font>
      <p>在pagesHelper包下的界面操作方法封装使得编写测试用例时，测试逻辑容易编写，在长期项目中，封装的界面操作方法复用性极高，不同的组合即可形成新的测试逻辑。</p>
  </div>
</el-card>
      
</template>

<script>
export default 
{
  name: 'dataTables',
  data () {
    return {
      multipleSelection: [],
      url:"https://gitee.com/xiaolanyun/DevOps_AppiumTest",//Appium测试框架
      imgSrc1:'./static/images/Appium.png',
      imgSrc2:'./static/images/AppiumDesign.png',
      imgSrc3:'./static/images/AppiumProject.png',
    }
  },
  methods: 
  {
    toggleSelection (rows) 
    {
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
    getuser(){
        window.setTimeout("window.open('https://gitee.com/xiaolanyun/DevOps_AppiumTest')", 1000); 
    },
    getmp4(){
      window.setTimeout("window.open('https://gitee.com/xiaolanyun/DevOps_AppiumTestMp4')",1000);
    }
  },
  // mounted() {
  //   this.getuser()
  //   }
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

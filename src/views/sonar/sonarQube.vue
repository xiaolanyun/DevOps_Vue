<<template>
    <div class="maven">
    <p  <i class="fa fa-spinner fa-pulse"/>请查看新打开的sonarQube窗口</p>
     
    </div>

</template>>

<script>

export default{
    name: 'maven',
    data(){

        return{
            //url:"http://192.168.222.128:8081/",
            html: "<b style='color:red'>v-html</b>"
        }
    },
    methods: {
      requestData (url) {
        const self = this;
        if (url && url.length > 0) {
        let param = {
        accept: 'text/html, text/plain'
        }
        self.$http.get(url, param).then((response) => {
          // 处理HTML显示
            self.html = response.data;
            }).catch(() => {
              self.html = '加载失败';
              })
        }
      },
      // 也可以通过 params 对象传递参数
      getuser(){
        window.setTimeout("window.open('http://192.168.222.130:9000/projects')", 2000); 
        // window.open('http://192.168.222.130:9000/projects');
      }
    },
    mounted() {
    //this.requestData("http://192.168.222.128:8081/");
    this.getuser()
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

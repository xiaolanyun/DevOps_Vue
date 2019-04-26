<<template>
    <div class="maven">
      <p <i class="fa fa-spinner fa-pulse"></i>请查看新打开的Nexus窗口</p>
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
        // const Http = new  XMLHttpRequest();
        // Http.open("GET", url);
        // Http.send();
        // Http.onreadystatechange = (e)=>{
        //   if(Http.readyState == 4 && Http.status == 200) {
                
        //   const self = this;
        //   this.html = Http.responseText;
        //   console.log(Http.responseText);
        //     }
        // }
      },
      // 也可以通过 params 对象传递参数
      getuser(){
        window.setTimeout("window.open('http://192.168.222.128:8081/')",2000);
        // window.open('http://192.168.222.128:8081/');
　//self.href = 'http://192.168.222.128:8081/';

// this.axios.get('http://192.168.222.128:8081/', {
// })
// .then(function (response) {
// console.log(response);
// })
// .catch(function (error) {
// console.log(error);
// });
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
    font-size: 30px;
    color: #5e6d82;
    line-height: 1.5em;
  }
</style>

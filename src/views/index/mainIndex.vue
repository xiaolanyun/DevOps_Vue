// 主页
<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="8">
        <div class="card kjfs">
          <p class="title"><i class="fa fa-th-large fa-lg"></i>快捷方式</p>
          <ul>
            <li>
              <router-link to="/zentaoProduct" class="kjfs kjfs-bluee">
                <span><i class="el-icon-document fa-2x"></i></span>
                <span>项目管理平台</span>
              </router-link>
            </li>

            <li>
              <router-link to="/codeMayun" class="kjfs kjfs-pinkk">
                <span><i class="el-icon-share fa-2x"></i></span>
                <span>托管平台</span>
              </router-link>
            </li>

            <li>
              <router-link to="/jenkinsMain" class="kjfs kjfs-yelloww">
                <span><i class="el-icon-setting fa-2x"></i></span>
                <span>持续集成平台</span>
              </router-link>
            </li>
          </ul>
          <ul>
            <li><router-link to="/sonarQube" class="kjfs kjfs-grennn"><span><i class="el-icon-question fa-2x"></i></span><span>代码质量管理平台</span></router-link></li>
            <li><router-link to="/openFalcon" class="kjfs kjfs-purplee"><span><i class="el-icon-view fa-2x"></i></span><span>分布式系统监控</span></router-link></li>
            <li><router-link to="/mavenPrivateService" class="kjfs kjfs-lightBluee"><span><i class="el-icon-news fa-2x"></i></span><span>Maven仓库</span></router-link></li>
          </ul>

          <ul>
            <li><router-link to="/gitbookwiki" class="kjfs kjfs-grennn"><span><i class="el-icon-edit fa-2x"></i></span><span>知识沉淀</span></router-link></li>
          </ul>
        </div>
      </el-col>

      <el-col :span="7"></el-col>

     <el-col :span="9">
        <div class="card bbxx">
          <p class="title"><i class="fa fa-server"></i>版本信息</p>
          <div class="table">
            <p><span class="tit">当前版本</span>v2.0.0</p>
            <!-- <p><span class="tit">基于框架</span>vue2.0 + element-ui</p> -->
            <p><span class="tit">主要特色</span>基于DevOps思想使开发测试运维协作便捷化</p>
            <!-- <p><span class="tit">获取渠道</span>
                <span class="gitbox">
                  <a target="_blank" href="https://github.com/Nirongxu/vue-xuAdmin.git"><el-button type="primary" icon="el-icon-download" size="small">github</el-button></a>
                  <a target="_blank" href="https://gitee.com/nirongxu/xu-webplatform.git"><el-button type="primary" icon="el-icon-download" size="small">码云</el-button></a>
                </span>
            </p> -->
          </div>
        </div>
      </el-col>

      
    </el-row>
        
    <!-- <el-row>
      <el-col :span="24">
        <line-echarts id="lineEcharts" height="300px" ref="echarts"></line-echarts>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="24">
        <maintable id="maintable"></maintable>
      </el-col>
    </el-row> -->
  </div>
</template>

<script>
import LineEcharts from '../../components/ECharts/lineEcharts'
import Maintable from '../table/maintable'
export default {
  name: 'mainIndex',
  components: {Maintable, LineEcharts},
  mounted () {
    this.selfAdaption()
  },
  methods: {
    // echart自适应
    selfAdaption () {
      let that = this
      setTimeout(() => {
        window.onresize = function () {
          if (that.$refs.echarts) {
            that.$refs.echarts.chart.resize()
          }
        }
      }, 10)
    }
  }
}
</script>

<style lang="scss">
  $top:top;
  $bottom:bottom;
  $left:left;
  $right:right;
  $leftright: ($left, $right);
  $pinkk: #eec2d3;
  $bluee: #409eff;
  $yelloww: #f4d884;
  $grennn: #89dda0;
  $purplee: #78a2ea;
  $lightBluee: #b8d6ff;

  $list: bluee pinkk yelloww grennn purplee lightBluee;
  $list1: $bluee $pinkk $yelloww $grennn $purplee $lightBluee;
  %shadow{
    background: #fff;
    -webkit-box-shadow: 4px 4px 40px rgba(0, 0, 0, 0.2);
    box-shadow: 4px 4px 40px rgba(0, 0, 0, 0.2);
    border-color: rgba(0, 0, 0, 0.2);
    .title{
      font-size: 14px;
      padding: 10px;
      i{
        margin-#{$right}: 5px;
      }
    }
  }

  @mixin flex($direction:row,$content:space-between){
    display: flex;
    flex-direction: $direction;
    justify-content: $content;
  }
  .card{
    color: #666;
    @extend %shadow;

    ul{
      @include flex;
      li{
        flex: 1;
        a{
          color: #666666;
          align-items:center;
          padding-#{$top}: 20px;
          padding-#{$bottom}: 20px;
          @include flex(column);
          span{
            height: 44px;
          }
          .num{
            line-height: 44px;
            font-size: 42px;
            color: $bluee;
            margin: 0px;
          }
        }
        .kjfs-bluee{
          color: $bluee;
        }
        .kjfs-pinkk{
          color: $pinkk;
        }
        .kjfs-yelloww{
          color: $yelloww;
        }
        .kjfs-grennn{
          color: $grennn;
        }
        .kjfs-purplee{
          color: $purplee;
        }
        .kjfs-lightBluee{
          color: $lightBluee;
        }
        &:hover{
          .kjfs-bluee{
            color: #ffffff;
            background: $bluee;
          }
          .kjfs-pinkk{
            color: #ffffff;
            background: $pinkk;
          }
          .kjfs-yelloww{
            color: #ffffff;
            background: $yelloww;
          }
          .kjfs-grennn{
            color: #ffffff;
            background: $grennn;
          }
          .kjfs-purplee{
            color: #ffffff;
            background: $purplee;
          }
          .kjfs-lightBluee{
            color: #ffffff;
            background: $lightBluee;
          }
        }
      }
    }
    .table{
      padding: 21px;
      p{
        height: 52px;
        line-height: 52px;
        border: 1px solid #cccccc;
        overflow: hidden;
        border-#{$top}: none;
        @include flex( null,start);
        &:first-child{
          border-#{$top}: 1px solid #cccccc;
        }
        span{
        }
        .tit{
          width: 90px;
          min-width: 90px;
          height: 100%;
          text-align: center;
          border-#{$right}: 1px solid #cccccc;
          margin-#{$right}: 18px;
        }
        span.gitbox{
          flex: 1;
          height: 100%;
          overflow: hidden;
          @include flex(row,start);
          a{
            &:first-child{
              margin-#{$right}: 30px;
            }
          }
        }
      }
    }
  }
  #lineEcharts{
    margin-#{$top}: 30px;
    padding-#{$top}: 30px;
    @extend %shadow;
  }
  #maintable{
    margin-#{$top}: 30px;
    padding-#{$top}: 10px;
    @extend %shadow;
  }
</style>

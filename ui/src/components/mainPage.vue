<template>
  <div class="main">
    <div class="searchBar" id="searchBar">
      <el-menu
        :default-active="activeIndex"
        :style="{'padding-left': menuLeft + 'px'}"
        mode="horizontal"
        @select="handleSelect"
        background-color="#545c64"
        text-color="#fff"
        :center="true"
        active-text-color="#ffd04b">
        <el-menu-item index="1">首页</el-menu-item>
        <el-submenu index="2">
          <template slot="title">技术杂谈</template>
          <el-menu-item index="2-1">选项1</el-menu-item>
          <el-menu-item index="2-2">选项2</el-menu-item>
          <el-menu-item index="2-3">选项3</el-menu-item>
          <el-submenu index="2-4">
            <template slot="title">选项4</template>
            <el-menu-item index="2-4-1">选项1</el-menu-item>
            <el-menu-item index="2-4-2">选项2</el-menu-item>
            <el-menu-item index="2-4-3">选项3</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title">文章转载</template>
          <el-menu-item index="3-1">选项1</el-menu-item>
          <el-menu-item index="3-2">选项2</el-menu-item>
          <el-menu-item index="3-3">选项3</el-menu-item>
          <el-submenu index="3-4">
            <template slot="title">选项4</template>
            <el-menu-item index="3-4-1">选项1</el-menu-item>
            <el-menu-item index="3-4-2">选项2</el-menu-item>
            <el-menu-item index="3-4-3">选项3</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-menu-item index="4">个人归档</el-menu-item>
        <el-menu-item index="5">我的项目</el-menu-item>
        <el-menu-item index="6">给我留言</el-menu-item>
        <el-menu-item index="7">关于我</el-menu-item>
      </el-menu>
    </div>
    <div class="content" :class="edit?'editable':'diseditable'">
      <div class="title">
        <el-form :inline="true" :model="formInline" class="demo-form-inline" style="margin-left: 10px">
          <el-form-item  v-if="!edit">
            文章标题
          </el-form-item>
          <el-form-item label="标题" v-if="edit">
            <el-input v-model="formInline.user" placeholder="文章标题"></el-input>
          </el-form-item>
          <el-form-item label="二级标题" v-if="edit">
            <el-select v-model="formInline.region" placeholder="二级标题">
              <el-option label="区域一" value="shanghai"></el-option>
              <el-option label="区域二" value="beijing"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="一级标题" v-if="edit">
            <el-select v-model="formInline.region" placeholder="一级标题">
              <el-option label="区域一" value="shanghai"></el-option>
              <el-option label="区域二" value="beijing"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item label="标签 " v-if="edit">
            <el-select v-model="formInline.region" placeholder="标签">
              <el-option label="区域一" value="shanghai"></el-option>
              <el-option label="区域二" value="beijing"></el-option>
            </el-select>
          </el-form-item>
          <el-form-item class="btns">
            <div>
              <el-button v-if="!edit" @click="changeEdit">编辑</el-button>
              <el-button v-if="edit" @click="save">保存</el-button>
            </div>
          </el-form-item>
        </el-form>
        标题


      </div>
      <editor :editBlog="edit"/>
    </div>

  </div>
</template>

<script>
  import editor from './editor'
export default {
  name: 'mainPage',
  components:{
    editor
  },
  data () {
    return {
      activeIndex: '1',
      menuLeft:  (document.body.clientWidth-700)/2,
      edit: false,
      formInline: {
        user: '',
        region: ''
      }
    }
  },
  created() {

  },
  mounted(){
    window.onresize = () => {
      return (() => {
        this.menuLeft = (document.body.clientWidth - 700) / 2;
      })()
    }
  },
  methods:{
    save(){
      this.edit = false;
    },
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    },
    changeEdit() {
      this.edit = true;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .el-menu--horizontal>.el-menu-item{
    width: 100px;
    text-align: center;
  }
  .content{
    margin-top: 10px;
    box-shadow: 0 0px 4px rgba(0,0,0,0.157), 0 0px 4px rgba(0,0,0,0.227);
  }
  .btns{
    float: right;
  }
  .diseditable{
    width: 60%;
    margin-left: 20%;
  }
  .editable{
    width: 80%;
    margin-left: 10%;
  }
  .title{
    height: 60px;
    line-height: 60px;
    width: 100%;
    background-color: gray;
  }

</style>

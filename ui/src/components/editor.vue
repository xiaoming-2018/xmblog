<template>
  <div class="editor">
    <!--<mavon-editor :style="{height: editorHeight + 'px'}" class="editor" v-model="msg" :toolbarsFlag="toolbarsFlag" :subfield="subfield" :defaultOpen="defaultOpen"/>-->
    <mavon-editor :style="{height: editorHeight + 'px'}" class="editor" v-model="msg" :toolbars="toolbars" :toolbarsFlag="toolbarsFlag" :subfield="subfield"
                  :defaultOpen="defaultOpen" @previewToggle="toggle"/>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: '# Welcome to Your Vue.js App',
      toolbars: {
        bold: true, // 粗体
        italic: true, // 斜体
        header: true, // 标题
        underline: true, // 下划线
        strikethrough: true, // 中划线
        mark: true, // 标记
        superscript: true, // 上角标
        subscript: true, // 下角标
        quote: true, // 引用
        ol: true, // 有序列表
        ul: true, // 无序列表
        link: true, // 链接
        imagelink: true, // 图片链接
        code: false, // code
        table: true, // 表格
        fullscreen: true, // 全屏编辑
        readmodel: true, // 沉浸式阅读
        // htmlcode: true, // 展示html源码
        help: true, // 帮助
        /* 1.3.5 */
        undo: false, // 上一步
        redo: false, // 下一步
        trash: true, // 清空
        // save: false, // 保存（触发events中的save事件）
        /* 1.4.2 */
        navigation: true, // 导航目录
        /* 2.1.8 */
        alignleft: true, // 左对齐
        aligncenter: true, // 居中
        alignright: true, // 右对齐
        /* 2.2.1 */
        subfield: true, // 单双栏模式
        preview: true, // 预览
      },
      toolbarsFlag: false, // 是否显示工具栏
      subfield: false, // 是否双栏
      // menuLeft:  (document.body.clientWidth-700)/2,
      searchBarFixed: false,
      defaultOpen: 'preview',
      editorHeight: document.documentElement.clientHeight - 140
    }
  },
  props:{
    editBlog:{
      type: Boolean,
      default: true
    }
  },
  watch:{
    editBlog(val){
      if(val === true){
        this.subfield = true;
        this.toolbarsFlag = true
      }else{
        this.subfield = false;
        this.toolbarsFlag = false


      }

    }
  },
  created() {

  },
  mounted(){
    window.onresize = () => {
      return (() => {
        console.log(111)
        this.editorHeight = document.documentElement.clientHeight - 140
        this.menuLeft = (document.body.clientWidth - 700) / 2;
      })()
    }
  },
  methods:{
    save(){
      console.log(this.msg)
    },
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    },
    toggle(){
      console.log('toggle')
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

</style>

<!--  -->
<template>
  <div class="play">
    <el-tag size="medium" class="title">打豆豆组件</el-tag>
    <Input @addItem="addItem" />
    <Item :thingsList="sortList" @updateFun="updateFun" @deleteFun="deleteFun">
    </Item>
  </div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
import Input from "../components/Input";
import Item from "../components/Item";
export default {
  //import引入的组件需要注入到对象中才能使用
  components: {
    Input,
    Item
  },
  data() {
    //这里存放数据
    return {
      list: [
        { checked: false, title: "学习vuex" },
        { checked: true, title: "吃烤鸭" }
      ]
    };
  },
  //监听属性 类似于data概念
  computed: {
    sortList() {
      return this.list.sort((a, b) => a.checked - b.checked);
    }
  },
  //监控data中的数据变化
  watch: {},
  //方法集合
  methods: {
    addItem(val) {
      this.list.push(val);
    },
    updateFun(index) {
      this.list[index].checked = !this.list[index].checked;
    },
    deleteFun(index) {
      this.list.splice(index, 1);
    }
  },
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {},
  beforeCreate() {}, //生命周期 - 创建之前
  beforeMount() {}, //生命周期 - 挂载之前
  beforeUpdate() {}, //生命周期 - 更新之前
  updated() {}, //生命周期 - 更新之后
  beforeDestroy() {}, //生命周期 - 销毁之前
  destroyed() {}, //生命周期 - 销毁完成
  activated() {} //如果页面有keep-alive缓存功能，这个函数会触发
};
</script>
<style scoped lang='stylus'>
.play {
  width: 570px;
  margin: 0 auto;

  .title {
    margin-bottom: 20px;
    transform: scale(1.4);
  }
}
</style>
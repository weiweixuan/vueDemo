<template>
  <div class="item">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>工作表</span>
        <!-- <el-button style="float: right; padding: 3px 0" type="text"
          >操作按钮</el-button
        > -->
      </div>
      <div
        v-for="(o, index) in this.thingsList"
        :key="o.title"
        class="text item flex"
      >
        <div :class="o.checked ? 'checked' : 'noChecked'">{{ o.title }}</div>
        <div>
          <el-button
            type="primary"
            icon="el-icon-edit"
            circle
            @click="updateFun(index)"
          ></el-button>
          <el-button
            type="danger"
            icon="el-icon-delete"
            circle
            @click="deleteFun(index)"
          ></el-button>
        </div>
      </div>
    </el-card>
  </div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';

export default {
  //import引入的组件需要注入到对象中才能使用
  components: {},
  data() {
    //这里存放数据
    return {};
  },
  props: ["thingsList"],
  //监听属性 类似于data概念
  computed: {},
  //监控data中的数据变化
  watch: {},
  //方法集合
  methods: {
    updateFun(index) {
      this.$emit("updateFun", index);
    },
    deleteFun(index) {
      this.$emit("deleteFun", index);
    }
  },
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {
    console.log(this.thingsList);
  },
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
.item {
  margin-top: 10px;
}

.flex {
  display: flex;
  justify-content: space-between;
  align-items: center;

  .checked {
    &::before {
      content: '已完成';
      color: green;
      margin-right: 20px;
    }
  }

  .noChecked {
    &::before {
      content: '未完成';
      margin-right: 20px;
      color: red;
    }
  }
}
</style>
<template>

<grid>
  <am-col sm="12" md="12" lg="12">
  <h1>button组件总是使用button标签，而且type总是为button，如果要使用a标签的button，需要自定义</h1>
  </am-col>
  <am-col sm="12" md="12" lg="12">
    <ambutton></ambutton>
    <ambutton type="primary" v-on="click: alert" lg>主色按钮</ambutton>
    <ambutton type="secondary" radius xs>次色小圆角按钮</ambutton>
    <ambutton type="success" disabled round sm>绿色禁用椭圆按钮</ambutton>
    <ambutton type="warning" round loading="{{@ isLoading }}" v-on="click: submitNow">{{ isLoading ? '正在提交……' : '橙色椭圆按钮' }}</ambutton>
    <ambutton type="danger" active xl>红色大激活按钮</ambutton>
    <ambutton block type="primary">块状按钮</ambutton>
  </am-col>
  <am-col sm="12" md="12" lg="12">
    <ambutton-group>
      <ambutton></ambutton>
      <ambutton></ambutton>
      <ambutton></ambutton>
      <ambutton></ambutton>
      <ambutton></ambutton>
    </ambutton-group>
  </am-col>
  <am-col sm="12" md="12" lg="12">
    <a v-link="{ path: '/' }">返回首页</a>
  </am-col>
</grid>

</template>

<script>

var amaze = require('amaze');

module.exports = {

  components: {
    "grid": amaze.grid.grid,
    "column": amaze.grid.column,
    "ambutton": amaze.button.button,
    "ambuttonGroup": amaze.button.buttonGroup
  },

  data: function() {
    return {
      isLoading: false
    };
  },

  methods: {
    "alert": function() {
      alert('yeah~');
    },
    "submitNow": function() {
      this.isLoading = true;
      var vm = this;
      setTimeout(function() {
        vm.isLoading = false;
      }, 3000);
    }
  }

};

</script>

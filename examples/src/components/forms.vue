<template>

<am-grid>
  <am-col sm="12" md="6" lg="8">
    <am-form submit="{{submit}}">
      <alert closed="{{ alertClosed }}" style="warning" closeable v-ref="alert">我是提示，只显示一次，关了就没了</alert>
      <am-input type="email" name="email" placeholder="请输入邮箱" model="{{@ form.email }}">邮箱</am-input>
      <am-input name="nick" placeholder="请输入昵称" model="{{@ form.nick }}">昵称</am-input>
      <am-input name="nick2" placeholder="请输入昵称" disabled model="{{@ form.nick2 }}">被禁用</am-input>
      <am-input type="password" name="passwd" placeholder="请输入密码" model="{{@ form.passwd }}">密码</am-input>
      <am-checkbox
        name="when"
        items="{{[{label: '加蛋', value: 1}, {label: '加饭', value: 2}, {label: '加汤', value: 3}]}}"
        model="{{@ form.when }}">
      </am-checkbox>
      <am-radio name="type" items="{{ [{label: '中通', value: 1}, {label: '圆通', value: 2}, {label: '申通', value: 3}] }}" model="{{@ form.type }}"></am-radio>
      <am-select label="时间" name="when2" items="{{ [{label: '上午', value: 1}, {label: '中午', value: 2}, {label: '下午', value: 3}] }}" model="{{@ form.when2 }}"></am-select>
    </am-form>
  </am-col>
  <am-col sm="12" md="6" lg="4">
    <a v-link="{path: '/'}">返回首页</a>
  </am-col>
</am-grid>

</template>

<script>

var amaze = require('amaze');

module.exports = {

  ready: function() {
    // var alert = this.$.alert;
    // setTimeout(function() {
    //   alert.close();
    // }, 3000);
  },

  components: {
    "amGrid": amaze.grid.grid,
    "amCol": amaze.grid.col,
    "amForm": amaze.form.form,
    "amInput": amaze.form.input,
    "amCheckbox": amaze.form.checkbox,
    "amRadio": amaze.form.radio,
    "amSelect": amaze.form.select,
    "alert": amaze.alert
  },

  data: function() {
    return {
      form: {
        email: '',
        nick: '',
        nick2: '',
        passwd: '',
        when: '',
        type: '',
        when2: ''
      }
    };
  },

  methods: {
    submit: function(event) {
      event.preventDefault();
      console.log(this.form);
      return false;
    },
    alertClosed: function() {
      alert('调用closed的时候还没有完全销毁');
    }
  }

};

</script>

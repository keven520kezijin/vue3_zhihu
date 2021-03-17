<template>
  <!-- <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div> -->
  <div class="container">
    <global-header :user="currentUser" />
    <form>
      <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">邮箱地址{{emailVal}}</label>
        <validate-input
          :rules="emailRules"
          v-model="emailVal"
          class="kv"
          placeholder="请输入邮箱地址"
          type="text"
        />
      </div>
      <div class="mb-3">
        <label for="exampleInputPassword1" class="form-label">密码</label>
        <validate-input
          :rules="epasswordRules"
          v-model="epasswordVal"
          placeholder="请输入密码"
          type="password"
        />
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <column-list :list="list" />
  </div>
  <!-- <router-view/> -->
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import ValidateInput, { RulesProp } from './components/ValidateInput.vue'
import 'bootstrap/dist/css/bootstrap.min.css'
import ColumnList, { ColumnProps } from './components/ColumnList.vue'
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
const currentUser: UserProps = {
  isLogin: true,
  name: 'keven'
}

const testData: ColumnProps[] = [
  {
    id: 1,
    title: 'test1的专栏',
    description: '这是的test专栏，有一段非常有意思的简介，可以更新一下哦',
    avatar: 'https://tva1.sinaimg.cn/large/007wciQDgy1fzvlvmua6ij30lg0qoq4g.jpg'
  }, {
    id: 2,
    title: 'test2的专栏',
    description: '这是的test专栏，有一段非常有意思的简介，可以更新一下哦'
    // avatar: 'https://cn.vuejs.org/images/logo.png'
  }, {
    id: 1,
    title: 'test1的专栏',
    description: '这是的test专栏，有一段非常有意思的简介，可以更新一下哦',
    avatar: 'https://cn.vuejs.org/images/logo.png'
  }, {
    id: 2,
    title: 'test2的专栏',
    description: '这是的test专栏，有一段非常有意思的简介，可以更新一下哦',
    avatar: 'https://cn.vuejs.org/images/logo.png'
  }
]

export default defineComponent({
  name: 'App',
  components: {
    ColumnList,
    GlobalHeader,
    ValidateInput
  },
  setup () {
    const emailVal = ref('957314724@qq.com')
    const emailRules: RulesProp = [
      { type: 'required', message: '电子邮箱地址不能为空' },
      { type: 'email', message: '请输入正确的电子邮箱格式' }
    ]
    const passwordVal = ref('')
    const passwordRules: RulesProp = [
      { type: 'required', message: '密码不能为空' }
    ]
    return {
      list: testData,
      currentUser,
      emailRules,
      emailVal,
      passwordVal,
      passwordRules
    }
  }
})
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

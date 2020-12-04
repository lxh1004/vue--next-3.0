<template>
  <div class="home">
    <ul>
      <li v-for="item in stus" :key="item.id">{{ item.val }}</li>
    </ul>

    <p>{{ count }}</p>
    <p>
      <el-button @click="add" type="primary">添加</el-button>
      <el-button @click="remove" type="danger">删除</el-button>
    </p>

    <ul>
      <li v-for="item in arr" :key="item">{{ item }}</li>
    </ul>
    <p>biaozhu tongji peizhi</p>
  </div>
</template>

<script>
import { ref, reactive, getCurrentInstance } from 'vue'
export default {
  name: 'Home',

  setup() {
    const { ctx } = getCurrentInstance()
    console.log(ctx, '替代后的this')
    //ref函数注意点
    //ref函数只能监听 简单类型的变化， 不能监听复杂类型的变化（对象|数组）
    //reactive可以监听复杂类型的数据变化

    const count = ref(0)
    const arr = reactive([1, 2, 3, 4])
    const add = () => {
      count.value++
    }

    function remove() {
      count.value--
    }

    let stus = reactive([
      {
        id: 1,
        val: 'zs',
      },
      {
        id: 2,
        val: 'ls',
      },
      {
        id: 3,
        val: 'ww',
      },
    ])

    return {
      stus,
      count,
      add,
      remove,
      arr,
    }
  },
}
</script>

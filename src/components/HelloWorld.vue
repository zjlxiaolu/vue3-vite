<template>
    <h1>{{ lu.name }}</h1>
    <hr />
    <h1>{{ lu2.name }}</h1>
    <hr>
    <h1>{{ obj }}</h1>
    <button @click="change">点击</button>
</template>

<script setup lang="ts">
/*
 * 检测复杂类型的数据 :Ref<>
 * 普通类型检测可以用 ref<>
 * isRef 判断一个属性是不是ref对象
 * ref 和 shallowRef 不能同时使用，会影响到 shallowRef 同时进行更新
 */
import { ref, isRef, shallowRef, reactive } from 'vue'
import type { Ref } from 'vue'

type L = {
    name: string
}

const lu: Ref<L> = ref({ name: '小路' })
const lu2 = shallowRef({ name: '小路2' })
const obj = reactive({ count: 0 })

function change() {
    lu.value.name = '大路'
    lu2.value.name = '大路2'
    console.log('lu', lu)
    console.log('lu2', lu2)
    console.log('lu 是不是一个ref', isRef(lu))
    obj.count++
}
</script>

<style scoped>
.read-the-docs {
    color: #888;
}
</style>

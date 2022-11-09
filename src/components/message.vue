<template >
    <el-button :plain="true" @click="openb">Show message</el-button>
    <el-button :plain="true" @click="openVn">VNode</el-button>
    <br><br><br>
    <el-button :plain="true" class="btn" @click="open2">成功</el-button>
    <el-button  :plain="true" @click="open3">测试动画</el-button>
    <el-button :plain="true" @click="open1">message</el-button>
    <el-button :plain="true" @click="open4">error</el-button>
    <br><br>
    <div >
        <el-button text @click="open" >点击这里测试页面抖动情况</el-button>
    </div>
    <span>测试的时候记得让下面的表格也显露出来，那个会受到影响</span>
</template>
  
<script lang="ts" setup>
import { h } from 'vue'
import { ElMessage, ElMessageBox } from 'element-plus'
import 'animate.css'
import animateCSS from '../tools/animateCSS ';



const openb = () => {
    ElMessage('this is a message.')
}

const openVn = () => {
    ElMessage({
        message: h('p', null, [
            h('span', null, 'Message can be '),
            h('i', { style: 'color: teal' }, 'VNode'),
        ]),
    })
}

const open1 = () => {
  ElMessage('this is a message.')
}
const open2 = () => {
    animateCSS('.btn', 'bounceIn')
  ElMessage({
    message: 'Congrats, this is a success message.',
    type: 'success',
  })
  
}
const open3 = () => {
  ElMessage({
    message: 'Warning, this is a warning message.',
    type: 'warning',
  })
}
const open4 = () => {
  ElMessage.error('Oops, this is a error message.')
}

const open = () => {
    animateCSS('.el-message-box', 'bounceIn')
  ElMessageBox.confirm(
    
    'proxy will permanently delete the file. Continue?',
    'Warning',
    {
      confirmButtonText: 'OK',
      cancelButtonText: 'Cancel',
      type: 'warning',
    }
  )
    .then(() => {
      ElMessage({
        type: 'success',
        message: '这个信息也会受到波及，左右晃动',
      })
    })
    .catch(() => {
      ElMessage({
        type: 'info',
        message: '这个信息也会受到波及，左右晃动',
      })
    })
}
</script>
<style>

</style>
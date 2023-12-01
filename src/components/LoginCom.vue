<template>
    <el-dialog v-model="IsShowLogin" title="登录" width="30%" :before-close="handleClose">
      <el-form :model="form" label-width="120px">
        <el-form-item label="用户名">
          <el-input v-model="form.UserName" />
        </el-form-item>
        <el-form-item label="密码">
          <el-input v-model="form.Password" type="password" show-password />
        </el-form-item>
        <el-form-item label="验证码">
          <el-input v-model="form.ValidateCode" />
          <el-image style="width: 200px; height: 100px"  />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="Submit">确定</el-button>
          <el-button @click="CloseLogin">取消</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
  </template>
  <script lang="ts" setup>
  import { computed, ref, onMounted } from "vue";
  import { useStore } from 'vuex'
  let ValidateKey = "";
  
  //vuex
  const store = useStore()
  const IsShowLogin = computed(() => store.state.IsShowLogin)
  const handleClose = (done: () => void) => {
    store.commit('CloseLogin')
    done();
  };
  const form = {
    UserName: "",
    Password: "",
    ValidateCode: ""
  }
  const Submit = async () => {
  }
  const CloseLogin = () => {
    store.commit('CloseLogin')
  }
  </script>
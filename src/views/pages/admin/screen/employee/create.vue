<script setup>
import { reactive } from 'vue';
import { useRouter } from 'vue-router';
import { useEmployeeStore } from '@/store/employee.js';
import dayjs from 'dayjs'; //import dayjs for date formatting

const { createVendor } = useEmployeeStore();
const router = useRouter();
const navigateBack = () => {
  router.go(-1);
};
// do not use same name with ref
const form = reactive({
  first_name: '',
  last_name: '',
  contact_number: '',
  email: '',
  password: '',
});
const onSubmit = async () => {
  try {
    await createVendor(form);
    router.go(-1);
  } catch (e) {
    console.error('Error creating vendor:', e);
  }
};
</script>

<template>
  <div class="form">
    <el-button type="warning" plain @click="navigateBack">
      <font-awesome-icon :icon="['fas', 'arrow-left']" />
      Back
    </el-button>
    <h1>Create Employee</h1>
    <el-form :model="form" label-width="auto">
      <el-form-item label="Firstname">
        <el-input v-model="form.first_name" placeholder="Enter your firstname" />
      </el-form-item>
      <el-form-item label="Lastname">
        <el-input v-model="form.last_name" placeholder="Enter your lastname" />
      </el-form-item>
      <el-form-item label="Contact">
        <el-input v-model="form.contact_number" placeholder="Enter your phone number" />
      </el-form-item>
      <el-form-item label="Email">
        <el-input v-model="form.email" placeholder="example@gmail.com" />
      </el-form-item>
      <el-form-item label="Password">
        <el-input v-model="form.password" show-password placeholder="Enter Password" />
      </el-form-item>
      <el-form-item class="gap-3">
        <el-button type="primary" @click="onSubmit">Create</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<style scoped>
h1 {
  font-size: 30px;
  justify-content: center;
  justify-items: center;
  text-align: center;
  margin-bottom: 10px;
}
.form {
  width: 800px;
  height: 800px;
  padding: 10px;
  border-radius: 20px;
}
.el-content {
  font-size: 20px;
}
</style>

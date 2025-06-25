<template>
  <aside class="sidebar bg-light d-flex flex-column justify-content-between p-3 border-end">
    <!-- Logo -->
    <div class="d-flex flex-column">
      <div class="d-flex justify-content-center mb-4">
        <img src="@/assets/images/speediz-logo.png" alt="Project Logo" class="w-75" />
      </div>

      <!-- Navigation -->
      <el-menu :default-active="$route.path" class="w-100 bg-light" router>
        <el-menu-item index="/admin/dashboard" class="nav-item">
          <el-icon>
            <Clock />
          </el-icon>
          <span>Dashboard</span>
        </el-menu-item>

        <el-menu-item index="/admin/vendor-list" class="nav-item">
          <el-icon>
            <List />
          </el-icon>
          <span>Vendor List</span>
        </el-menu-item>

        <el-sub-menu index="invoice">
          <template #title>
            <el-icon>
              <Document />
            </el-icon>
            <span>Invoice</span>
          </template>
          <el-menu-item index="/admin/package-invoice" class="nav-item">Package Invoice</el-menu-item>
          <el-menu-item index="/admin/vendor-invoice" class="nav-item">Vendor Invoice</el-menu-item>
        </el-sub-menu>

        <el-menu-item index="/admin/tracking" class="nav-item">
          <el-icon>
            <Location />
          </el-icon>
          <span>Tracking</span>
        </el-menu-item>

        <el-sub-menu index="user-management">
          <template #title>
            <el-icon>
              <User />
            </el-icon>
            <span>User Management</span>
          </template>
          <el-menu-item index="/admin/vendor" class="nav-item">Vendor</el-menu-item>
          <el-menu-item index="/admin/delivery" class="nav-item">Delivery</el-menu-item>
          <el-menu-item index="/admin/employee" class="nav-item">Employee</el-menu-item>
        </el-sub-menu>

        <el-menu-item index="/admin/setting" class="nav-item">
          <el-icon>
            <Setting />
          </el-icon>
          <span>Setting</span>
        </el-menu-item>

        <el-menu-item index="/admin/logout" class="nav-item">
          <el-icon>
            <SwitchButton />
          </el-icon>
          <span>Logout</span>
        </el-menu-item>
      </el-menu>
    </div>
  </aside>
</template>

<script setup>
import { Clock, List, Document, Location, User, Setting, SwitchButton } from '@element-plus/icons-vue';
</script>

<style scoped>
.sidebar {
  width: 250px;
  height: 100vh;
  background-color: #f8f9fa; /* Bootstrap light background */
}

.el-menu-item.is-active {
  background-color: #ffc107 !important; /* Bootstrap warning color */
  color: #fff !important;
  border-radius: 10px;
}

.el-menu {
  width: 100%;
}
</style>

<script setup lang="js">
import { BDropdown, BDropdownItem, BDropdownHeader } from 'bootstrap-vue-next'
import SimpleBar from 'simplebar-vue'
import Logo from '../../../components/shared/Logo.vue'
</script>

<template>
  <li>
    <BDropdown
      variant="link"
      wrapper-class="dropdown-wrapper"
      toggle-class="dropdown-toggle"
      menu-class="dropdown-menu"
      no-caret
      aria-label="Profile"
    >
      <template #button-content>
        <a href="#" class="dropdown-toggle-inner" aria-label="Profile">
          <i class="ph ph-user-circle"></i>
        </a>
        <span class="visually-hidden">Profile</span>
      </template>
      <BDropdownHeader tag="div" header-class="dropdown-header">
        <div class="dropdown-header-content">
          <div class="avatar-wrapper">
            <img src="../../../assets/images/user/avatar-2.jpg" alt="user-image" class="user-avatar" />
          </div>
          <div class="user-info">
            <h6 class="user-name">Carson Darrin 🖖</h6>
            <span class="user-email">carson.darrin@company.io</span>
          </div>
        </div>
      </BDropdownHeader>
      <div class="dropdown-body">
        <SimpleBar style="max-height: calc(100vh - 225px); overflow-x: hidden" :options="{ autoHide: false }">
          <BDropdownItem href="#">
            <span>
              <Logo name="custom-setting-outline" class="icon" />
              <span>Settings</span>
            </span>
          </BDropdownItem>
          <BDropdownItem href="#">
            <span>
              <Logo name="custom-share-bold" class="icon" />
              <span>Share</span>
            </span>
          </BDropdownItem>
          <BDropdownItem href="#">
            <span>
              <Logo name="custom-lock-outline" class="icon" />
              <span>Change Password</span>
            </span>
          </BDropdownItem>
          <div class="logout-wrapper">
            <button class="logout-button">
              <Logo name="custom-logout-1-outline" class="icon" />
              Logout
            </button>
          </div>
        </SimpleBar>
      </div>
    </BDropdown>
  </li>
</template>

<style scoped>
.dropdown-wrapper {
  position: relative;
}
.dropdown-toggle {
  background: none;
  border: none;
  padding: 0;
}
.dropdown-toggle-inner {
  display: inline-flex;
  align-items: center;
}
.dropdown-menu {
  right: 0;
  left: auto;
  padding: 0;
  overflow: hidden;
}
.dropdown-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #0d6efd;
  padding: 12px;
}
.dropdown-header-content {
  display: flex;
  margin: 8px 0;
}
.avatar-wrapper {
  flex-shrink: 0;
}
.user-avatar {
  width: 35px;
  height: 35px;
  border-radius: 50%;
}
.user-info {
  flex-grow: 1;
  margin-left: 12px;
}
.user-name {
  color: #fff;
  margin-bottom: 4px;
  font-size: 14px;
}
.user-email {
  color: rgba(255, 255, 255, 0.75);
  font-size: 12px;
}
.icon {
  margin-right: 8px;
  vertical-align: text-bottom;
  color: #6c757d;
}
.logout-wrapper {
  display: grid;
  margin: 12px 0;
}
.logout-button {
  background-color: #0d6efd;
  border: none;
  color: #fff;
  padding: 8px 12px;
  border-radius: 4px;
  font-size: 14px;
  display: inline-flex;
  align-items: center;
}
</style>

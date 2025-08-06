<script setup lang="js">
import { BDropdown, BDropdownHeader, BDropdownText, BCard } from 'bootstrap-vue-next'
import SimpleBar from 'simplebar-vue'
</script>

<template>
  <li>
    <BDropdown
      variant="link"
      wrapper-class="dropdown-wrapper"
      toggle-class="dropdown-toggle"
      menu-class="dropdown-menu"
      no-caret
      aria-label="Notification"
    >
      <template #button-content>
        <a href="#" class="dropdown-toggle-inner" aria-label="Notification">
          <i class="ph ph-bell"></i>
          <span class="notification-badge">3</span>
        </a>
        <span class="visually-hidden">Notification</span>
      </template>

      <BDropdownHeader tag="h5" header-class="dropdown-header">
        <h5 class="header-title">Notifications</h5>
        <a href="#!" class="mark-read-btn">Mark all read</a>
      </BDropdownHeader>

      <SimpleBar style="height: calc(100vh - 215px); overflow-x: hidden" :options="{ autoHide: false }">
        <div class="dropdown-body">
          <BDropdownText text="Today" text-class="section-label" tag="p" />
          <BDropdownText text-class="notification-card">
            <BCard class="card-wrapper">
              <div class="card-content">
                <div class="avatar-wrapper">
                  <img class="avatar" src="../../../assets/images/user/avatar-1.jpg" alt="avatar" />
                </div>
                <div class="card-info">
                  <span class="time">2 min ago</span>
                  <h5 class="title">UI/UX Design</h5>
                  <p class="description">
                    Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type
                  </p>
                </div>
              </div>
            </BCard>
          </BDropdownText>

          <BDropdownText text-class="notification-card">
            <BCard class="card-wrapper">
              <div class="card-content">
                <div class="avatar-wrapper">
                  <img class="avatar" src="../../../assets/images/user/avatar-2.jpg" alt="avatar" />
                </div>
                <div class="card-info">
                  <span class="time">1 hour ago</span>
                  <h5 class="title">Message</h5>
                  <p class="description">
                    Lorem Ipsum has been the industry's standard dummy text ever since the 1500.
                  </p>
                </div>
              </div>
            </BCard>
          </BDropdownText>

          <BDropdownText text="Yesterday" text-class="section-label" tag="p" />

          <BDropdownText text-class="notification-card">
            <BCard class="card-wrapper">
              <div class="card-content">
                <div class="avatar-wrapper">
                  <img class="avatar" src="../../../assets/images/user/avatar-3.jpg" alt="avatar" />
                </div>
                <div class="card-info">
                  <span class="time">2 hour ago</span>
                  <h5 class="title">Forms</h5>
                  <p class="description">
                    Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type
                  </p>
                </div>
              </div>
            </BCard>
          </BDropdownText>

          <BDropdownText text-class="notification-card">
            <BCard class="card-wrapper">
              <div class="card-content">
                <div class="avatar-wrapper">
                  <img class="avatar" src="../../../assets/images/user/avatar-4.jpg" alt="avatar" />
                </div>
                <div class="card-info">
                  <span class="time">12 hour ago</span>
                  <h5 class="title">Challenge invitation</h5>
                  <p class="description">
                    <span class="username">Jonny aber</span> invites to join the challenge
                  </p>
                  <button class="btn-secondary">Decline</button>
                  <button class="btn-primary">Accept</button>
                </div>
              </div>
            </BCard>
          </BDropdownText>

          <BDropdownText text-class="notification-card">
            <BCard class="card-wrapper">
              <div class="card-content">
                <div class="avatar-wrapper">
                  <img class="avatar" src="../../../assets/images/user/avatar-5.jpg" alt="avatar" />
                </div>
                <div class="card-info">
                  <span class="time">5 hour ago</span>
                  <h5 class="title">Security</h5>
                  <p class="description">
                    Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type
                  </p>
                </div>
              </div>
            </BCard>
          </BDropdownText>
        </div>
      </SimpleBar>

      <BDropdownText text-class="dropdown-footer">
        <a href="#!" class="clear-btn">Clear all Notifications</a>
      </BDropdownText>
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
}
.dropdown-toggle-inner {
  display: inline-flex;
  align-items: center;
  position: relative;
}
.notification-badge {
  position: absolute;
  top: -4px;
  right: -6px;
  background: #28a745;
  color: #fff;
  font-size: 10px;
  padding: 2px 5px;
  border-radius: 50%;
}
.dropdown-menu {
  right: 0;
  left: auto;
  width: 360px;
}
.dropdown-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px;
}
.header-title {
  font-size: 16px;
  font-weight: 600;
  margin: 0;
}
.mark-read-btn {
  font-size: 13px;
  text-decoration: none;
  color: #0d6efd;
}
.dropdown-body {
  padding: 0 12px;
}
.section-label {
  font-size: 12px;
  font-weight: 600;
  padding: 12px 0 4px;
  margin: 0;
}
.notification-card {
  padding: 0;
  margin-bottom: 12px;
}
.card-wrapper {
  background-color: #fff;
  border: none;
  box-shadow: none;
}
.card-content {
  display: flex;
  padding: 12px;
}
.avatar-wrapper {
  flex-shrink: 0;
}
.avatar {
  width: 45px;
  height: 45px;
  border-radius: 6px;
}
.card-info {
  flex-grow: 1;
  margin-left: 12px;
}
.time {
  float: right;
  font-size: 12px;
  color: #6c757d;
}
.title {
  margin: 6px 0;
  font-size: 15px;
}
.description {
  font-size: 13px;
  margin: 0;
}
.username {
  font-weight: 600;
  color: #000;
}
.btn-primary {
  background-color: #0d6efd;
  border: none;
  color: white;
  font-size: 12px;
  padding: 4px 8px;
  margin-top: 8px;
  margin-right: 6px;
}
.btn-secondary {
  background-color: transparent;
  border: 1px solid #6c757d;
  color: #6c757d;
  font-size: 12px;
  padding: 4px 8px;
  margin-top: 8px;
  margin-right: 6px;
}
.dropdown-footer {
  text-align: center;
  padding: 12px 0;
}
.clear-btn {
  color: #dc3545;
  text-decoration: none;
  font-size: 13px;
}
</style>

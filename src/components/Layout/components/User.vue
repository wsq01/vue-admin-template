<template>
  <div class="user-avatar-dropdown">
    <Dropdown @on-click="handleClick">
      <Avatar :src="userAvatar"/>
      <Icon :size="18" type="md-arrow-dropdown"></Icon>
      <DropdownMenu slot="list">
        <DropdownItem name="logout">退出登录</DropdownItem>
      </DropdownMenu>
    </Dropdown>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'User',
  props: {
    userAvatar: {
      type: String,
      default: ''
    }
  },
  methods: {
    ...mapActions([
      'handleLogOut'
    ]),
    logout () {
      this.handleLogOut().then(() => {
        this.$router.push({
          name: 'login'
        })
      })
    },
    handleClick (name) {
      switch (name) {
        case 'logout': this.logout()
          break
      }
    }
  }
}
</script>

<style lang="less" scoped>
.user{
  &-avatar-dropdown{
    cursor: pointer;
    display: inline-block;
    // height: 64px;
    vertical-align: middle;
    // line-height: 64px;
    .ivu-badge-dot{
      top: 16px;
    }
  }
}
</style>

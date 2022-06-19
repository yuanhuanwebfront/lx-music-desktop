<template>
<div :class="$style.menu">
  <ul class="menu-ul" :class="$style.list" role="toolbar">
    <li v-for="item in menus" :key="item.to" :class="$style.navItem" role="presentation">
      <router-link class="router-link" :class="$style.link" :active-class="$style.active" role="tab" :aria-selected="$route.name == item.to" :to="item.to" :aria-label="item.tips">
        <i class="iconfont" :class="item.icon"></i>
        <span>{{item.tips}}</span>
      </router-link>
    </li>
  </ul>
</div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  name: 'Nav',
  computed: {
    ...mapGetters(['setting']),
    menus() {
      return [
        {
          to: 'search',
          tips: this.$t('search'),
          icon: 'icon-sousuo',
          enable: true,
        },
        {
          to: 'songList',
          tips: this.$t('song_list'),
          icon: 'icon-gedan',
          enable: true,
        },
        {
          to: 'leaderboard',
          tips: this.$t('leaderboard'),
          icon: 'icon-paihangbang',
          enable: true,
        },
        {
          to: 'list',
          tips: this.$t('my_list'),
          icon: 'icon-geren',
          enable: true,
        },
        {
          to: 'download',
          tips: this.$t('download'),
          icon: 'icon-download',
          enable: this.setting.download.enable,
        },
        {
          to: 'setting',
          tips: this.$t('setting'),
          icon: 'icon-setting',
          enable: true,
        },
      ].filter(m => m.enable)
    },
  },
}
</script>

<style lang="less" module>
@import '@renderer/assets/styles/layout.less';

.menu {
  flex: auto;
}
.list {
  -webkit-app-region: no-drag;
  // margin-bottom: 15px;
  &:last-child {
    margin-bottom: 0;
  }
}

</style>

<style>
a.router-link{
  position: relative;
  display: flex;
  align-items: center;
  text-decoration: none;
  transition: 0.5s;
  height: 60px;
  line-height: 60px;
  padding: 0 20px;
  color: #6f778d;
  border-bottom: 1px solid #f6f6f6;
}
a.router-link:hover{
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px -1px, rgba(0, 0, 0, 0.06) 0px 2px 4px -1px;
}
a.router-link i{
  margin-right: 20px;
  font-size: 24px;
}
a.router-link i.icon-gedan{
  font-size: 26px;
}
a.router-link::after{
  width: 100%;
}
</style>

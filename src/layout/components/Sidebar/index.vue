<template>
  <div :class="{'has-logo':showLogo}">
    <logo v-if="showLogo" :collapse="isCollapse"/>

    <el-scrollbar wrap-class="scrollbar-wrapper">
      <div class="content-side content-side-full">
        <ul class="nav-main">
          <li class="nav-main-item">
            <a class="nav-main-link active">
              <!--              <i class="nav-main-link-icon si si-speedometer"></i>-->
              <svg-icon class="nav-main-link-icon si" icon-class="dashboard"/>
              <span class="nav-main-link-name">仪表盘</span>
            </a>
          </li>
          <li class="nav-main-item"><a class="nav-main-link false"><i
            class="nav-main-link-icon si el-icon-notebook-2"></i><span class="nav-main-link-name">使用文档</span></a>
          </li>
          <li class="nav-main-heading">订阅</li>
          <li class="nav-main-item"><a class="nav-main-link false"><i class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">我的订阅</span></a></li>
          <li class="nav-main-item"><a class="nav-main-link false"><i class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">购买订阅</span></a></li>
          <li class="nav-main-heading">财务</li>
          <li class="nav-main-item"><a class="nav-main-link false"><i class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">我的订单</span></a></li>
          <li class="nav-main-item"><a class="nav-main-link false"><i class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">我的邀请</span></a></li>
          <li class="nav-main-heading">用户</li>
          <li class="nav-main-item"><a class="nav-main-link false"><i class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">个人中心</span></a></li>
          <li class="nav-main-item"><a class="nav-main-link false"><i class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">我的工单</span></a></li>
          <li class="nav-main-item"><a class="nav-main-link false"><i
            class="nav-main-link-icon si el-icon-shopping-cart-1"></i><span
            class="nav-main-link-name">流量明细</span></a></li>
        </ul>
      </div>
    </el-scrollbar>
  </div>
</template>

<script>
  import {mapGetters} from 'vuex'
  import Logo from './Logo'
  import SidebarItem from './SidebarItem'
  import variables from '@/styles/variables.scss'

  export default {
    components: {SidebarItem, Logo},
    computed: {
      ...mapGetters([
        'sidebar'
      ]),
      routes() {
        return this.$router.options.routes
      },
      activeMenu() {
        const route = this.$route
        const {meta, path} = route
        // if set path, the sidebar will highlight the path you set
        if (meta.activeMenu) {
          return meta.activeMenu
        }
        return path
      },
      showLogo() {
        return this.$store.state.settings.sidebarLogo
      },
      variables() {
        return variables
      },
      isCollapse() {
        return !this.sidebar.opened
      }
    }
  }
</script>
<style scoped>

  .content-side {
    width: 100%;
    margin: 0 auto;
    padding: 1.125rem 1.125rem 1px;
    overflow-x: hidden;
  }

  .content-side.content-side-full {
    padding-bottom: 1.125rem
  }

  .content-side.content-side-full > .pull, .content-side.content-side-full > .pull-b, .content-side.content-side-full > .pull-y {
    margin-bottom: -1.125rem
  }

  .nav-main {
    padding-left: 0;
    list-style: none;
  }

  .nav-main-item {
    display: flex;
    flex-direction: column;
  }

  .nav-main-link.active, .nav-main-link:hover {
    color: #000;
    background-color: #e1effe;
  }

  .nav-main-link {
    position: relative;
    display: flex;
    align-items: center;
    padding: 0.5rem 0.625rem;
    margin: 2px 0;
    min-height: 2.25rem;
    font-size: 1rem;
    font-weight: 500;
    line-height: 1.25rem;
    letter-spacing: .0125em;
    color: #555d65;
    border-radius: 0.2rem;
  }

  .nav-main-link .nav-main-link-name {
    flex: 1 1 auto;
    display: inline-block;
    max-width: 100%;
  }

  .nav-main-link .nav-main-link-icon {
    flex: 0 0 auto;
    display: inline-block;
    margin-right: 0.625rem;
    min-width: 1.25rem;
    font-size: 1rem;
    text-align: center;
    color: rgba(6, 101, 208, .7);
  }

  .si {
    font-family: simple-line-icons;
    speak: none;
    font-style: normal;
    font-weight: 400;
    font-variant: normal;
    text-transform: none;
    line-height: 1;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  .nav-main-heading {
    padding-top: 1.75rem;
    padding-bottom: 0.25rem;
    padding-left: 0.625rem;
    font-size: 1.5rem;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: .075rem;
    color: #949da5;
  }
</style>

<template>
  <div class="wrapper" :class="{'nav-open': $sidebar.showSidebar}">
    <notifications></notifications>
    <side-bar>
      <user-menu></user-menu>
      <mobile-menu></mobile-menu>
      <template slot-scope="props" slot="links">

        <template v-if="userType == 1">
          <sidebar-item :link="{name: 'Анкета', icon: 'nc-icon nc-notes', path: '/forms/wizard'}"></sidebar-item>
          <sidebar-item :link="{name: 'Личный кабинет', icon: 'nc-icon nc-badge', path: '/pages/user'}"></sidebar-item>
          <sidebar-item :link="{name: 'Услуги', icon: 'nc-icon nc-settings-90'}">
            <sidebar-item :link="{name: 'Мои услуги', path: '/services/my'}"></sidebar-item>
            <sidebar-item :link="{name: 'Все услуги', path: '/services/list'}"></sidebar-item>
          </sidebar-item>
        </template>
        <template v-else-if="userType == 2">
          <sidebar-item :link="{name: 'Заявки', icon: 'nc-icon nc-bullet-list-67', path: '/orders/list'}"></sidebar-item>
        </template>
        <template v-else-if="userType == 3">
          <sidebar-item :link="{name: 'Администратор', icon: 'nc-icon nc-single-02'}">
            <sidebar-item :link="{name: 'Управление', path: '/admin/main'}"></sidebar-item>
          </sidebar-item>
          <sidebar-item :link="{name: 'Заявки', icon: 'nc-icon nc-bullet-list-67', path: '/orders/list'}"></sidebar-item>
          <sidebar-item :link="{name: 'Справочники', icon: 'nc-icon nc-grid-45'}">
            <sidebar-item :link="{name: 'Сертификаты', path: '/reference-books/sertificates'}"></sidebar-item>
            <sidebar-item :link="{name: 'Пользователи', path: '/reference-books/users'}"></sidebar-item>
            <sidebar-item :link="{name: 'Менеджеры', path: '/reference-books/managers'}"></sidebar-item>
            <sidebar-item :link="{name: 'Регионы', path: '/reference-books/regions'}"></sidebar-item>
            <sidebar-item :link="{name: 'Религии', path: '/reference-books/religions'}"></sidebar-item>
          </sidebar-item>
        </template>

        <hr>

        <!--<sidebar-item :link="{name: 'Dashboard', icon: 'nc-icon nc-chart-pie-35', path: '/admin/overview'}">-->
        <!--</sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Components', icon: 'nc-icon nc-app'}">-->
          <!--<sidebar-item :link="{name: 'Buttons', path: '/components/buttons'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Grid System', path: '/components/grid-system'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Panels', path: '/components/panels'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Sweet Alert', path: '/components/sweet-alert'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Notifications', path: '/components/notifications'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Icons', path: '/components/icons'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Typography', path: '/components/typography'}"></sidebar-item>-->
        <!--</sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Forms', icon: 'nc-icon nc-notes'}">-->
          <!--<sidebar-item :link="{name: 'Regular Forms', path: '/forms/regular'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Extended Forms', path: '/forms/extended'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Validation Forms', path: '/forms/validation'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Wizard', path: '/forms/wizard'}"></sidebar-item>-->
        <!--</sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Tables', icon: 'nc-icon nc-paper-2'}">-->
          <!--<sidebar-item :link="{name: 'Regular Tables', path: '/table-list/regular'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Extended Tables', path: '/table-list/extended'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Paginated Tables', path: '/table-list/paginated'}"></sidebar-item>-->
        <!--</sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Maps', icon: 'nc-icon nc-pin-3'}">-->
          <!--<sidebar-item :link="{name: 'Google Maps', path: '/maps/google'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Full Screen Maps', path: '/maps/full-screen'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Vector Maps', path: '/maps/vector-map'}"></sidebar-item>-->
        <!--</sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Charts', icon: 'nc-icon nc-chart-bar-32', path: '/admin/charts'}"></sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Calendar', icon: 'nc-icon nc-single-copy-04', path: '/admin/calendar'}"></sidebar-item>-->
        <!--<sidebar-item :link="{name: 'Pages', icon: 'nc-icon nc-puzzle-10'}">-->
          <!--<sidebar-item :link="{name: 'User Page', path: '/pages/user'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Login Page', path: '/login'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Register', path: '/register'}"></sidebar-item>-->
          <!--<sidebar-item :link="{name: 'Lock Screen Page', path: '/lock'}"></sidebar-item>-->
        <!--</sidebar-item>-->
      </template>
    </side-bar>
    <div class="main-panel">
      <top-navbar></top-navbar>

      <dashboard-content @click.native="toggleSidebar">

      </dashboard-content>

      <content-footer></content-footer>
    </div>
  </div>
</template>
<script>
  import TopNavbar from './TopNavbar.vue'
  import ContentFooter from './ContentFooter.vue'
  import DashboardContent from './Content.vue'
  import MobileMenu from './Extra/MobileMenu.vue'
  import UserMenu from './Extra/UserMenu.vue'
  export default {
    components: {
      TopNavbar,
      ContentFooter,
      DashboardContent,
      MobileMenu,
      UserMenu
    },
    computed: {
      userType() {
        return this.$store.state.userType
      }
    },
    methods: {
      toggleSidebar () {
        if (this.$sidebar.showSidebar) {
          this.$sidebar.displaySidebar(false)
        }
      }
    },
  }

</script>

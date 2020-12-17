<template>
  <header id="main-header">
    <div class="main-header">
      <b-container fluid>
        <b-row>
          <b-col sm="12">
            <nav class="navbar navbar-expand-lg navbar-light p-0">
              <a
                href="javascript:void(0)"
                class="navbar-toggler c-toggler collapsed"
                @click="openSidebar"
              >
                <div class="navbar-toggler-icon" data-toggle="collapse">
                  <span class="navbar-menu-icon navbar-menu-icon--top"></span>
                  <span
                    class="navbar-menu-icon navbar-menu-icon--middle"
                  ></span>
                  <span
                    class="navbar-menu-icon navbar-menu-icon--bottom"
                  ></span>
                </div>
              </a>
              <router-link class="navbar-brand" :to="homeURL">
                <img class="img-fluid logo" :src="logo" alt="streamit"
              /></router-link>
              <b-collapse id="navbarSupportedContent" is-nav :visible="sidebar">
                <div class="menu-main-menu-container">
                  <ul id="top-menu" class="navbar-nav ml-auto">
                    <li
                      v-for="(item, index) in items"
                      :key="index"
                      class="menu-item"
                      :style="{ order: `${index > 1 ? index + 1 : index}` }"
                    >
                      <router-link :to="item.link">{{
                        item.title
                      }}</router-link>
                    </li>
                    <li
                      class="menu-item nav-item nav-icon"
                      v-nav-toggle
                      style="order: 2"
                    >
                      <a
                        href="#"
                        class="iq-user-dropdown search-toggle p-0 d-flex align-items-center"
                        @mouseenter="showGamesModal = true"
                        @mouseleave="showGamesModal = false"
                      >
                        Games
                      </a>
                      <transition name="fade">
                        <div
                          class="iq-sub-dropdown iq-user-dropdown games-dropdown"
                          v-show="showGamesModal"
                          @mouseenter="showGamesModal = true"
                          @mouseleave="showGamesModal = false"
                        >
                          <span
                            @click="
                              $router.push({
                                path: '/game/Bruce',
                              })
                            "
                            >Bruce</span
                          >
                          <span
                            @click="
                              $router.push({
                                path: '/game/Bruce-Saves-Christmas',
                              })
                            "
                            >Bruce Saves Christmas</span
                          >
                        </div>
                      </transition>
                    </li>
                  </ul>
                </div>
              </b-collapse>
              <div class="mobile-more-menu">
                <b-navbar-toggle
                  target="dropdownMenuButton"
                  class="more-toggle"
                >
                  <i class="ri-more-line"></i>
                </b-navbar-toggle>
                <b-collapse id="dropdownMenuButton" class="more-menu">
                  <div class="navbar-right position-relative">
                    <slot name="responsiveRight" />
                  </div>
                </b-collapse>
              </div>
              <div class="navbar-right menu-right">
                <slot name="responsiveRight" />
              </div>
            </nav>
            <div class="nav-overlay"></div>
          </b-col>
        </b-row>
      </b-container>
    </div>
  </header>
</template>
<script>
import { core, APPLOGONAME } from '../../../config/pluginInit';
export default {
  name: 'FrontendNav',
  props: {
    homeURL: {
      type: Object,
      default: () => ({ name: 'landing-page.landing-page' }),
    },
    logo: { type: String, default: require('../../../assets/images/logo.png') },
    items: { type: Array },
    userprofile: { type: String },
  },
  data() {
    return {
      appName: APPLOGONAME,
      sidebar: false,
      showGamesModal: false,
    };
  },
  mounted() {
    core.index();
    document.addEventListener('click', this.closeSidebar, true);
  },
  destroyed() {
    document.removeEventListener('click', this.closeSidebar, true);
  },
  methods: {
    //  goTo(name) {
    //    return this.$router.push({ path: `game/${name}` });
    //  },
    closeSidebar(e) {
      if (!e.target.classList.contains('navbar-toggler-icon')) {
        this.sidebar = false;
        document.getElementsByTagName('body')[0].classList.remove('nav-open');
      }
    },
    openSidebar() {
      document.getElementsByTagName('body')[0].classList.add('nav-open');
      this.sidebar = true;
    },
  },
};
</script>

<style lang="scss" scoped>
#top-menu {
  display: flex;
  justify-content: center;
  // align-items: center;
}
.games-dropdown {
  position: absolute;
  right: 0;
  top: 60px;
  background-color: #191919;
  // height: 100px;;
  width: auto;
  padding: 20px 20px 20px 50px;
  display: flex;
  justify-content: flex-start;
  flex-direction: column;
  // border: 1px solid red;
  // transition: all 0.3s ease-in-out;
  // max-width: 50px !important;
  span {
    white-space: nowrap;
    text-align: start;
    cursor: pointer;
    padding: 2px 0;
    &:hover {
      color: red;
    }
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease-in-out;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>

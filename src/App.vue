<template>
  <v-ons-page>
    <v-ons-toolbar>
      <div class="header-left left" v-show="last" :style="styleToolbar()" @click="popPage">
        <v-ons-button modifier="quiet" v-if="ios">
          <v-ons-icon size="25px" icon="ion-chevron-left"></v-ons-icon> Back
        </v-ons-button>
        <v-ons-button modifier="quiet" v-else>
          <v-ons-icon size="25px" icon="md-arrow-left"></v-ons-icon>
        </v-ons-button>
      </div>
      <div class="center header-title">{{ title }}</div>
      <div class="right toolbar__right" :style="styleToolbar()"></div>
    </v-ons-toolbar>

    <v-ons-tabbar position="auto"
      :tabs="tabs"
      :visible="true"
      ref="Nav"
      :index.sync="activeIndex"
      @postchange="changeTab"
      @backButton="backButton"
    >
    </v-ons-tabbar>
  </v-ons-page>
</template>

<script>
  import settingsPage from 'Settings';

  import newsPage from 'News';
  import Home from 'Home';
  import Nav from 'Nav';

  export default {
    data() {
      return {
        activeIndex: 0,
        last: null,
        ios: this.$ons.platform.isIOS(),
        tabs: [
          {
            icon: this.md() ? null : 'ion-home',
            label: 'Home',
            page: Nav,
            key: 'Home',
            props: {
              list: {
                extends: Home,
                data() {
                  return {};
                }
              }
            }
          },
          {
            icon: this.md() ? null : 'ion-ios-bell',
            label: 'News',
            page: Nav,
            key: 'News',
            props: {
              list: {
                extends: newsPage,
                data() {
                  return {
                  }
                }
              }
            }
          },
          {
            icon: this.md() ? null : 'ion-ios-settings',
            label: 'Settings',
            page: Nav,
            key: 'Settings',
            props: {
              list: {
                extends: settingsPage,
                data() {
                  return {
                  }
                }
              }
            }
          }
        ]
      };
    },
    methods: {
      md() {
        return this.$ons.platform.isAndroid();
      },
      backButton(pageStack) {
        this.last = pageStack[pageStack.length - 2];
      },
      styleToolbar() {
        return `display: ${this.last ? 'inline' : 'none'}`;
      },
      changeTab() {
        this.backButton(this.$refs.Nav.$children[this.activeIndex].$data.pageStack);
      },
      popPage(e) {
        this.$refs.Nav.$children[this.activeIndex].$data.pageStack.pop();
        this.backButton(this.$refs.Nav.$children[this.activeIndex].$data.pageStack);
      }
    },
    computed: {
      title() {
        return this.tabs[this.activeIndex].label;
      }
    },
    components: { homePage, settingsPage, newsPage }
  }
</script>

<style>
.header-title {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  position: relative;
  width: 100%;
}
</style>
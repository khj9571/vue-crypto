<template>
  <v-app id="inspire">
    <v-navigation-drawer width="370" v-model="drawer" app clipped>
      <side-menu :drawer.sync="drawer"></side-menu>
    </v-navigation-drawer>

    <v-app-bar app color="indigo" dark clipped-left>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container class="fill-height" fluid>
        <v-layout column>
            <router-view></router-view>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer color="indigo" app>
      <span class="white--text">&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<style lang="scss">
.example {
  background-color: $content_color;
  color: $font_color;
}
</style>


<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import SideMenu from "@/components/layouts/SideMenu.vue";
import TabMenu from "@/components/layouts/TabMenu.vue";
import Loading from "@/components/global/Loading.vue";
import { loadingEvents, LOADINGEVENT } from "@/events/Events";
import { State, Action, Getter, Mutation } from "vuex-class";

@Component({
  components: {
    SideMenu,
    Loading,
    TabMenu
  }
})
export default class App extends Vue {
  @Getter("getIsLogin") getIsLogin: any;
  @Getter("getUserInfo") getUserInfo: any;
  @Mutation("clearLogout") clearLogout: any;

  drawer = null;

  visible = false;

  dialog = false;

  get currentUrl() {
    return this.$route.path;
  }
  //
  created() {
    //loadingEvents.$on('')

    loadingEvents.$on(LOADINGEVENT.SHOW, () => {
      this.visible = true;
    });

    loadingEvents.$on(LOADINGEVENT.HIDE, () => {
      this.visible = false;
    });
  }

  mounted() {
    // this.$vuetify.theme.themes.dark.primary = "#4caf50";
    this.$vuetify.theme.dark = true;
  }

  onListItemClick(item: any) {
    if (item == 0) {
      this.dialog = true;
    }
  }
}
</script>



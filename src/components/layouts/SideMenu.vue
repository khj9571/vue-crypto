<template>
  <v-container fluid grid-list-md v-border>
    <v-layout column wrap>
      <!-- class="mx-auto" max-width="500" -->
      <v-card fill-height v-border>
        <v-tabs v-model="tab" background-color="transparent" color="basil" grow fill-height> 
          <v-tab v-for="item in items" :key="item.key">{{ item.label }}</v-tab>
        </v-tabs>

        <v-tabs-items v-model="tab" fill-height>
          <v-tab-item :key="1" fill-height> 
            <v-card color="basil" flat fill-height>
              <v-card-text>1 </v-card-text>
            </v-card>
          </v-tab-item>
         <v-tab-item :key="2" fill-height>
            <v-card color="basil" flat fill-height>
              <v-card-text>2 </v-card-text>
            </v-card>
          </v-tab-item>
        </v-tabs-items>
      </v-card>
    </v-layout>
  </v-container>
</template>

<script lang="ts">
import { Component, Prop, Vue, PropSync, Ref } from "vue-property-decorator";
import { State, Action, Getter, Mutation } from "vuex-class";
import { cloneDeep, values, every, remove } from "lodash";
import { menuTabChangeEvents, MENUTABCHANGEEVENT } from "@/events/Events";

@Component({
  name: "side-menu",
  components: {}
})
export default class SideMenu extends Vue {
  @Ref("tree_menu") tree_menu: any;

  @PropSync("drawer", {
    // default: () => {
    //   return new Date();
    // }
    default: false
  })
  sync_drawer!: Boolean;

  private items = [{label:'거래소 목록',key:1},{label:'보유자산',key:2}]

  private tab = null

  onMenuClick() {}
}
</script>

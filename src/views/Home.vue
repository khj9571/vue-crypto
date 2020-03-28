<template>
  <!-- <HelloWorld /> -->
  <!-- <loading/> -->
  <v-container fluid fill-height>
    <v-layout align-center justify-center>
      <v-flex fill-height v-border>
        <v-card fill-height v-border>
          <v-toolbar dark fill-height>
            <v-toolbar-title>Login</v-toolbar-title>
          </v-toolbar>
         
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import { State, Action, Getter } from "vuex-class";

@Component({
  components: {}
})
export default class Home extends Vue {

 
  @Action("loginUser") loginUser: any;


  private userInfo: any = {
    userId: "1",
    userPw: "1"
  };

  mounted() {
    console.log(this);
  }

  onLoginClick() {


      this.loginUser(this.userInfo).then((res:any) => {


      })
      // if(this.userInfo.userId == 1 && this.userInfo.userPw == 1){
      //     alert('로그인 성공')
      // }else {
      //     alert('로그인 에러')
      // }

  }
}
</script>


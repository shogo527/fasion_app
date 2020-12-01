<template>
  <div class="log in">
    <Header></Header>
    <div v-show="!signup_vesible">
      <Signin></Signin>
    </div>
    <!--基本的にはSigninにしといてアカウントを持っている人にはSignupを表示させるようにする -->

    <div v-show="signup_vesible">
      <Signup></Signup>
    </div>
    <div>

      <button class="btn" v-on:click="signup_vesible = !signup_vesible">
        新規作成／ログイン
      </button>
    </div>
  </div>
</template>

<script>
import firebase from "firebase";
import Signup from "@/components/Signup.vue";
import Signin from "@/components/Signin.vue";
import Header from "../components/header";

export default {
  components: {
    Signup,
    Signin,
    Header
  },
  data() {
    return {
      signup_vesible: false,
      user: null,
      email: null,
      password: null
    };
  },

  methods: {
    addUser(info) {
      console.log(info);
      this.$store.dispatch("addUser", info);
    },

    authState() {
      firebase.auth().onAuthStateChanged(user => {
        console.log("authが実行");
        if (user) {
          // User is signed in.
          this.addUser(user);
          this.user = user;
        } else {
          // No user is signed in.
          this.addUser(null);
          this.user = null;
        }
      });
    }
  }
};
</script>

<style scoped>
.btn {
  background-color: rgb(96, 211, 146);
  border-radius: 50px 50px 50px 50px;
  width: 400px;
  height: 50px;
  color: white;
  font-size: 18px;
  margin-top: 90px;
}
.message {
  font-size: 6px;
  margin-top: 150px;
  text-align: left;
  padding-left: 30px;
}
</style>

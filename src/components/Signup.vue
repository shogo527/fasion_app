<template>
  <div>
    <div class="moji">新規登録会員</div>
    <p>
      メールアドレス
      <input v-model="email" class="form-control email-form" type="email" />
    </p>
    <p>
      パスワード
      <input
        v-model="password"
        class="form-control password-form"
        type="password"
      />
    </p>
    <button v-on:click="Signup" class="button">登録</button>
  </div>
</template>
<style scoped></style>
<script>
import firebase from "firebase";
export default {
  data() {
    return {
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

    Signup() {
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .catch(function(error) {
          // Handle Errors here.
          var errorCode = error.code;
          var errorMessage = error.message;
          console.log(errorCode);
          console.log(errorMessage);
        });
    },

    authState() {
      firebase.auth().onAuthStateChanged(user => {
        console.log("authが実行");
        if (user) {
          // User is signed in.
          this.addUser(user);
          this.user = user;
          this.$router.push("/");
        }
      });
    }
  },
  created() {
    this.authState();
  }
};
</script>

<style scoped>

.moji{
  display: inline-block;
  font-size: 40px;
  padding-bottom: 20px;
  color: gray;
}
.email-form {
  justify-content: center;
  border-radius: 50px 50px 50px 50px;
  width: 800px;
  height: 50px;
  background-color: rgb(235, 235, 235);
}
.password-form {
  justify-content: center;
  border-radius: 50px 50px 50px 50px;
  width: 800px;
  height: 50px;
  background-color: rgb(235, 235, 235);
}
.button {
  border-radius: 50px 50px 50px 50px;
  width: 210px;
  height: 70px;
  background-color: rgb(105, 169, 186);
  color: white;
  font-size: 26px;
  margin-top: 40px;
}
</style>

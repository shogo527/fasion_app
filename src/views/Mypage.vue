<template>
  <div>
    <Header></Header>
    <h1 id ="mypage">Mypage</h1>
    <div>
      <img id = "pic" src="@/assets/prof.png" alt />
      <h1>Shogo</h1>
      <p>ユーザー名: {{ this.account }}</p>
      <p>性別: {{ this.gender}}</p>
      <P>身長: {{ this.height }} cm</P>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
import Header from "../components/header";
import Footer from "../components/footer";
export default {
  data() {
    return {
      user: {},
      name: "Shogo",
      account: "@shogo__527",
      gender: "男",
      height: 170,
    };
  },
  components: {
    Header,
    Footer
  }
};
</script>

 <style scoped>
#mypage{

  font-size: 50px;
 }
#pic {
  width: 200px;
}

 </style>

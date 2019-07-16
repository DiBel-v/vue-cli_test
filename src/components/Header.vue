<template>
  <header class = "profile">
    <div class = "profile_leftblock">
      <div class = "profile__avatar">
        <img src="require(`@/assets/${imgName}`)">
      </div>
      <div class = "profile__company">
        <p class = "profile__company_name"  v-bind = "companyName">{{companyName}}</p>
        <p class = "profile__company_tagline" v-bind = "tagline">{{tagline}}</p>
      </div>
    </div>
    <div class = "profile_rightblock">
      <div class = "profile__naming">
        <p class = "profile__naming_name" v-bind = "personName">{{personName}}</p>
      </div>
      <button class = "profile__home"><img src = "@/assets/exit.png"></button>
    </div>
  </header>
</template>


<script>
  export default{
  data () {
    return {
      counter: 0,
      imageName: {
        'background-image': `url('../assets/${this.picture}.jpeg')`
      },
      companyName: "Название компании",
      tagline: "Слоган компании",
      personName: "Фамилия И.О."
    }
  }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.profile{
  font-family:'Times New Roman', Times, serif;
  font-size: 20px;
  display: flex;
  align-items: center;
  background-color: white;
  height: 100px;
  width: 100%;
 }
 .profile_leftblock{ 
   margin-left: 20px;
   margin-right: auto;
   display: flex;
 }
 .profile_rightblock{
   display: flex;
   margin-right: 20px;
 }
.profile__avatar{
  height: 40px;
  width: 40px;
  border: 2px solid gray;
  border-radius: 50%;
  background-color: lightgray;
  display: flex;
  margin: auto;
  padding: 20px;
}
.profile__avatar img{
  max-width: 40px;
  max-height: 40px;
}
.profile__company{
  margin-left: 10px;
  display: inline;
}
.profile__naming{
  text-align: center;
  float: left;
}
.profile__home{
  border-style:solid;
  background-color: white;
  border-radius: 5px;
  margin: auto;
  margin-left: 20px;
  height: 35px;
  width: 50px;
}

.profile__home img{
  width: 40px;
  height: 30px;
}

.profile__company_name{
  margin-bottom: 0;
  text-align: left;
}
.profile__company_tagline{
  text-align: left;
  font-size: 17px;
  margin-top: 0;
}
</style>

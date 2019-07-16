<template>
  <div id="app">
    <Header id = "head"/>
    <Menu :info="info" id = "menu" @newRoad="updateRoad" @newRGN="updateRGN" @newDist="updateDist"/>
    <Content :info="info" id = "content" :nameRoad="nameRoad" :nameRGN = "nameRGN" :nameDist="nameDist"/>
  </div>
</template>

<!-- получаем api, пишем апдейты для полей -->
<script>
import Header from './components/Header.vue'
import Menu from './components/Menu.vue'
import Content from './components/Content.vue'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    Header,
    Menu,
    Content
  },
  data() {
    return{
      info: [],
      errors: [],
      nameRoad: "",
      nameRGN: "",
      nameDist: ""
    };
  },
  mounted(){
    var self = this;
    axios.get("https://test-task.lexfoxer.now.sh/api/roads").then(response => {
      self.info = response.data.data;
      console.log('Data', response.data.data);
    })
    .catch(e => {
      self.errors.push(e);
    })
  },
  methods: {
    updateRoad(newRoad) {
      this.nameRoad = newRoad;
    },
    updateRGN(newRGN) {
      this.nameRGN = newRGN;
    },
    updateDist(newDist){
      this.nameDist = newDist;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 0;
  margin: 10px 20px 10px 20px;
  height: 90%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between
}
#head{
  flex: 0 1 100%;
}
#menu{
  flex: 0 0 25%;
}
#content{
  flex: 0 0 74%;
}
#check{
  background-color: white;
}
</style>

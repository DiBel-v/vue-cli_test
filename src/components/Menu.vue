<template>
 <aside class = "menu">
  <div class="menu__road">
    <label>Название дороги</label>
    <input type="text" placeholder="Пример поля в фокусе" @keyup.enter="searchRoad" v-model = "nameRoad">
  </div>
  <div class="menu__rgn">
    <label>РГН</label>
    <input type="text" @keyup.enter="searchRGN" v-model="nameRGN">
  </div>
  <div class="menu__city">
    <label>Городской округ</label>
    <select v-model = "nameDist" v-on = "searchDist">
        <option value="" disabled>Выберите из списка</option>
        <option v-for = "inf in info" :key = "inf.id" v-bind:value="inf.district_title">{{inf.district_title}}</option>
    </select>
  </div>
 </aside>
</template>


<!-- При изменении названия дороги, ргн, или городского округа изменяем и передаем в компоненты -->
<script>
  export default{
    name: "Menu",
    props: ['info'],
    data(){
      return{
        nameRoad: "",
        nameRGN: "",
        nameDist: ""
      };
    },
    methods: {
      searchRoad: function() {
      this.$emit("newRoad", this.nameRoad);
      this.nameRoad = "";
    },
      searchRGN: function() {
      this.$emit("newRGN", this.nameRGN);
      this.nameRGN = "";
    },
      searchDist: function() {
      this.$emit("newDist", this.nameDist);
      this.nameDist = "";
    }
    }
  }
</script>

<style scoped>
  .menu{
    color: gray;
    margin-top: 20px;
    background-color: white;
    height: 500px;
  }
  input{
    border-style:solid;
    border-radius: 5px;
    border-color: lightgray;
    text-indent: 10px;
  }
  input:hover{
    border-width: 1px;
    border-color: #0066ff;
  }
  div{
    margin-top: 20px;
  }
  .menu__road{
    margin-left: 20px;
    display: block;
  }
  .menu__road label{
    text-align: left;
    display: block;
  }
  .menu__road input{
    margin-top: 10px;
    line-height: 30px;
    width: 95%;
    display: block;
  }

  .menu__rgn{
    margin-left: 20px;
    display: block;
  }
  .menu__rgn label{
    text-align: left;
    display: block;
  }
  .menu__rgn input{
    margin-top: 10px;
    line-height: 30px;
    width: 95%;
    display: block;
  }

    .menu__city{
    margin-left: 20px;
    display: block;
  }
  .menu__city label{
    text-align: left;
    display: block;
  }
  .menu__city select{
    color: gray;
    margin-top: 10px;
    border-radius: 5px;
    height: 36px;
    width: 95.5%;
    display: block;
    text-indent: 10px;
  }
</style>
<template>
 <main class = "content">
  <table v-if = "info.length" class = "content__table">
    <thead>
      <tr>
        <th>Название</th>
        <th>РГН</th>
        <th>Городской округ</th>
        <th>ОКАТО</th>
      </tr>
    </thead>
    <tbody>
      <!-- Динамично добавить строки при условии, что одно из полей заполнено в точности, как в API
          (нужно было разделить еще на несколько if, через v-else-if не получилось, слишком много одинакового кода)-->
      <tr class = "info" v-for="inf in info" :key="inf.id" 
          v-if= "(nameRoad == inf.title && nameRoad != null) || (nameRGN == inf.rgn && nameRGN != null) || (nameDist == inf.district_title && nameDist != null)" >
        <td>{{inf.title}}</td>
        <td>{{inf.rgn}}</td>
        <td>{{inf.district_title}}</td>
        <td>{{inf.district_okato}}</td>
      </tr>
    </tbody>
    
  </table>
  
 </main>
</template>

<style scoped>
  .content{
    background-color: white;
    margin-top: 20px;
  }
  .content__table{
    margin:auto;
    margin-top: 20px;
  }
  .content__table td{
    border-bottom: 1px solid lightgray;
    padding: 20px 20px 20px 20px;
    text-align: left;
  }
    .content__table th{
      padding: 20px 20px 20px 20px;
      text-align: left;
      color: lightgray;
      border-bottom: 1px solid lightgray;
  }
</style>


<!-- Получаем пропсы из других компонентов-->
<script>
export default{
  props: ['info', 'nameRoad','nameRGN', 'nameDist'],
  data() {
    return{
      limit: 3,
      start: 0,
    };
  }
}

</script>
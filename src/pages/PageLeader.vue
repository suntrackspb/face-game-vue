<template>
  <div>
    <table class="table" v-if="response">
      <thead>
        <tr>
          <th>Имя</th>
          <th class="right">🎮</th>
          <th class="right">❓</th>
          <th class="right">🏆</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in response" :key="item._id">
          <td>{{ item._id }}</td>
          <td class="right">{{ item.total_games }}</td>
          <td class="right">{{ item.total_questions }}</td>
          <td class="right">{{ item.total_correct_answers }}</td>
        </tr>
      </tbody>
    </table>
    <p v-else>Loading...</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PageLeader",
  data() {
    return {
      response: null
    };
  },
  created() {
    axios.get('http://192.168.0.100:5000/api/v1/leader')
        .then(response => {
          // console.log(response.data)
          let array = response.data.board;
          array.sort((a, b) => b.total_correct_answers - a.total_correct_answers);
          this.response = array
        })
        .catch(error => {
          console.log(error);
        });
  }
}
</script>

<style scoped>
.app__table-container {
  width: 300px;
  margin: 20px auto;

}
.table {
  width: 342px;
  margin: 20px auto;
  border: none;
  border-collapse: separate;
  color: white;
}
.table thead th {
  font-weight: bold;
  text-align: left;
  border: none;
  padding: 10px 15px;
  background: darkviolet;
  color: #ffffff;
  font-size: 14px;
  border-top: 1px solid darkviolet;
}
.table tr th:first-child, .table tr td:first-child {
  border-left: 1px solid darkviolet;
}
.table tr th:last-child, .table tr td:last-child {
  border-right: 1px solid darkviolet;
}
.table thead tr th:first-child {
  border-radius: 10px 0 0 0;
}
.table thead tr th:last-child {
  border-radius: 0 10px 0 0;
}
.table tbody td {
  text-align: left;
  border: none;
  padding: 10px 15px;
  font-size: 14px;
  vertical-align: top;
}
.table tbody tr:nth-child(even) {
  background: #252525;
}
.table tbody tr:last-child td{
  border-bottom: 1px solid darkviolet;
}
.table tbody tr:last-child td:first-child {
  border-radius: 0 0 0 10px;
}
.table tbody tr:last-child td:last-child {
  border-radius: 0 0 10px 0;
}
.right {
  text-align: right !important;
}
</style>
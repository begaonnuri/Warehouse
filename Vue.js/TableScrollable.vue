<template>
  <div class="container">
    <div class="title">Title</div>
    <div class="table-container">
      <table>
        <thead>
          <tr class="table-header">
            <th style="width:10%">#</th>
            <th style="width:40%">내용</th>
            <th style="width:30%">비고</th>
            <th style="width:20%">날짜</th>
          </tr>
        </thead>
        <tbody>
          <tr class="table-content" v-for="(td, index) in tdList">
            <td>{{index+1}}</td>
            <td>{{td.content}}</td>
            <td>{{td.etc}}</td>
            <td>{{td.date}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tdList: [
        { content: "A", etc: "B", date: "C" },
        { content: "A", etc: "B", date: "C" },
        { content: "A", etc: "B", date: "C" }
      ]
    };
  }
};
</script>
<style>
.container {
  width: 500px;
  height: 300px;
  background-color: rgb(50, 58, 70);
  padding: 33px 30px;
  border-radius: 5px;
  cursor: default;
}
.title {
  font-size: 1rem;
  font-family: "Karla";
  color: #f7f7f7;
  font-weight: 600;
  margin: 0 0 15px 0px;
  display: inline-block;
}
.table-container {
  height: 300px;
  overflow: auto;
  font-size: 15px;
}
.table-container::-webkit-scrollbar {
  display: none !important;
}
.table-container table {
  width: 100%;
}
.table-header {
  color: rgb(0, 187, 153);
  text-align: center;
}
.table-header th {
  padding: 15px 20px;
}
.table-content {
  color: #f7f7f7;
  font-weight: lighter;
  text-align: center;
}
.table-content td {
  padding: 10px 0;
  border-top: 1px solid #555;
}
</style>
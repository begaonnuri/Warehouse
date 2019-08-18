<template>
  <div>
    <datetime v-model="date">
      <template slot="before">날짜</template>
      <template slot="button-cancel">취소</template>
      <template slot="button-confirm">확인</template>
    </datetime>
  </div>
</template>

<script>
import Datetime from "vue-datetime";
import "vue-datetime/dist/vue-datetime.css";

export default {
  data() {
    return {
      date: ""
    };
  },
  created() {
    // date input default를 오늘 날짜로 설정
    this.date = new Date().toISOString();
  }
};
</script>

<style>
.vdatetime {
  color: #f1f5f7;
  font-size: 15px;
  font-weight: 600;
  cursor: default;
}
.vdatetime-input {
  width: 130px;
  height: 38px;
  border: none;
  border-radius: 30px;
  background-color: rgba(50, 58, 70);
  cursor: pointer;
  margin-left: 5px;

  color: #f1f5f7;
  font-size: 14px;
  font-weight: 400;
  text-align: center;
}
.vdatetime-input:hover {
  background-color: rgba(170, 200, 190, 0.2);
  transition-duration: 0.8s;
}
</style>
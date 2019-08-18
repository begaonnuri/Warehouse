<template>
  <div class="list-container">
    <div class="list-nav-title">Title</div>
    <div class="list-nav-setting"></div>
    <div
      :class="{'list':true, 'active-list':currentViewId==item.id}"
      v-for="(item,index) in itemList"
      @click="emitItemInfo(item), setActiveItem(item)"
    >
      {{item.name}}
      <div :id="'icon'+index" class="icon"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 보여줄 List
      itemList: [
        { id: 1, name: "First item" },
        { id: 2, name: "Second item" },
        { id: 3, name: "Third item" }
      ],
      // 활성화 표시를 위한 변수
      currentViewId: 0
    };
  },
  methods: {
    setActiveItem: function(item) {
      this.currentViewId = item.id;
    },
    emitItemInfo: function(item) {
      this.$emit("emit-item", item);
    }
  }
};
</script>

<style>
.list-container {
  background-color: rgb(50, 58, 70);
  overflow-x: hidden;
  overflow-y: auto;
  height: 100%;
  width: 240px;
  position: fixed;
}
/* 스크롤 안보이지만 가능하도록 설정 */
#list-container::-webkit-scrollbar {
  display: none !important;
}
.list-nav-title {
  height: 70px;
  color: #f7f7f7;
  font-size: 18px;
  font-weight: 700;
  cursor: default;
  text-align: center;
  line-height: 70px;
  display: inline-block;
  margin-left: 80px;
}
.list-nav-setting {
  width: 20px;
  height: 20px;
  background-image: url(https://image.flaticon.com/icons/svg/126/126472.svg);
  -webkit-filter: invert(100%); /* 아이콘 반전(흰색 만들기위해)*/
  display: inline-block;
  vertical-align: middle;
  margin-bottom: 6px;
  margin-left: 5px;
  cursor: pointer;
}
.list {
  padding: 17px 20px;
  cursor: pointer;

  size: 0.925rem;
  color: #f7f7f7;
  font-family: "Roboto";
}
.list:hover {
  background-color: rgba(170, 200, 190, 0.2);
  transition-duration: 0.3s;
}
.active-list {
  background-color: rgba(170, 200, 190, 0.1);
}
.icon {
  width: 15px;
  height: 15px;
  border-radius: 20px;
  border: none;
  float: left;
  margin: 5px 20px 0 0;
  background-color: white;
}
</style>

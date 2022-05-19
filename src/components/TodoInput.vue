<template>
  <div class="inputBox shadow">
    <input type="text" v-model="searchKeyword" v-on:keyup.enter="addTodo" />
    <span class="addContainer" v-on:click="addTodo">
      <i class="fa-solid fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      searchKeyword: ""
    };
  },
  methods: {
    addTodo: function() {
      if (this.searchKeyword !== "") {
        let obj = { completed: false, item: this.searchKeyword };
        localStorage.setItem(this.searchKeyword, JSON.stringify(obj));
        this.clearInput();
      }
    },
    clearInput: function() {
      this.searchKeyword = "";
    }
  }
};
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478fb, #8763fb);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
.closeModalBtn {
  color: #42b983;
}
</style>

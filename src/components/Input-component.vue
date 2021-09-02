<template>
  <div>
      <input type="text" class="inputBox" v-model="message"><button class="addBtn" v-on:click="save">SAVE</button>
  </div>
</template>

<script>
export default {
    name: 'InputComponent',
    data() {
        return {
            message: ""
        }
    },
    methods: {
        save() {
            if(this.message !== '' && this.message !== 'loglevel:webpack-dev-server') {
                var jsonobj = {
                    "isChecked" : false,
                    "item" : this.message
                };
                localStorage.setItem(this.message, JSON.stringify(jsonobj));
                this.message = "";
            }
        }
    }
 }
</script>

<style>
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
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
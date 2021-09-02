<template>
  <div>
      <ul>
          <li v-for="(data, index) in list" :key="index">
              <span v-on:click="checkItem(index)" v-bind:class="{textCompleted : data.isChecked}">{{data.item}}</span>
              <span><button v-on:click="deleteItem(data.item)">del</button></span>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'ListComponent',
    props: ['list'],
    methods: {
        checkItem(index) {
            var jsonobj = this.list[index];
            console.log(jsonobj);
            jsonobj.isChecked = !jsonobj.isChecked;
            var obj = {
                    "isChecked" : jsonobj.isChecked,
                    "item" : jsonobj.item
                };

            for(var i = 0; i < localStorage.length; i++) {
                var key = localStorage.key(i);
                if(i === index) {
                    localStorage.removeItem(key);
                    localStorage.setItem(key, JSON.stringify(obj));
                }
                
            }
        },
        deleteItem(key) {
            localStorage.removeItem(key);
        }
    }
}
</script>

<style>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
</style>
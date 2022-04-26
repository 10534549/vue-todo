<template>
  <div class="todo">
    <div class="colorline"/>
    <div class="todobg"/>
    <div class="todotext"> {{ content }} </div>
    <div class="controlButtons">
      <button class="controlButtonDone material-icons" :class="{'controlButtonDoneCompleted': !progress}" @click="toggleTodo">done</button>
      <button class="controlButtonCancel material-icons" @click="rem">cancel</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  props: ['content', 'id', 'progress'],
  emits: ['changedProgress', 'remmed'],
  setup(props, { emit }){
    function toggleTodo(){
      emit('changedProgress', props.id)
    }
    function rem(){
      emit('remmed', props.id)
    }

    return{ toggleTodo, rem }
  }
}
</script>

<style scoped>
.todo{
  position: relative;
  height: 100px;
  width: 700px;
  margin: auto;
  text-align: center;
}
.todobg{
  position: absolute;
  top: 0;
  left: 1%;
  z-index: -1;
  margin: auto ;
  background: whitesmoke;
  border-radius: 20px;
  height: 100%;
  width: 99%;
}
.colorline{
  position: absolute;
  top: 2%;
  left: 0;
  margin: auto;
  z-index: -2;
  margin: auto ;
  background: coral;
  border-radius: 20px;
  height: 96%;
  width: 100%;
}
.todotext{
  margin-left: 8%;
  display: flex;
  justify-content: left;
  text-align: left;
  align-items: center;
  height: 100%;
  width: 67%;
}
.controlButtons{
  margin-right: 5%;
  position: absolute;
  top: 0;
  right: 0;
  width: 20%;
  height: 100%;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
.controlButtonDone,  .controlButtonCancel{
  color: black;
  cursor: pointer;
  padding: 0;
  margin: 0;
  border: none;
  text-align: center;
  background: whitesmoke;
  transition: all 0.2s ease;
}
.controlButtonDone:hover,  .controlButtonCancel:hover{
  transition: all 0.2s ease;
  transform: scale(1.2);
}
.controlButtonDoneCompleted{
  color: green;
}

.controlButtonCancel{
  color: red;
}

</style>
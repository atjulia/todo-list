<template>
  <div @click="$emit('taskStateChanged', task)" class="task" :class="stateClass">
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: { type: Object, required: true }
  },
  computed: {
    stateClass () {
      return {
        pending: this.task.pending,
        done: !this.task.pending
      }
    }
  }
}
</script>

<style>
  .task {
    position: relative;
    box-sizing: border-box;
    width: 900px;
    height: 80px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .pending {
    border-left: 12px solid #af1d3f;
    background-color: #eb3260;
  }

  .pending .close {
    background-color: #af1d3f;

  }

  .done {
    color: #fefefe;
    border-left: 12px solid #0b895d;
    background-color: #00c07d;
    text-decoration: line-through;
  }

  .done .close {
    background-color: #0b895d;
  }

  .close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
  }
</style>
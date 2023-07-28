<script setup>
import TodoContainer from "./views/TodoContainer.vue";
import Learning from "./practise/binding.vue";
</script>

<template>
    <div class="todo_wrapper_container">
        <TodoContainer />
        <Learning />
    </div>
</template>

<style>
body {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
}

.todo_wrapper_container {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100vw;
    height: 100vh;
    background-color: #fbb80f;
}
</style>

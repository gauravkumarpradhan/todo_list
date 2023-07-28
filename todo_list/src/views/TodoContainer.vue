<script>
import Card from "../components/card.vue";
export default {
    name: "TodoContainer",
    components: { Card },
    methods: {
        handleTodoItem: function (event) {
            if (event.key == "Enter") {
                this.addTodoItem(event.target.value);
                event.target.value = "";
            }
        },
        addTodoItem: function (value) {
            this.todoListItems.push({ todoItemTitle: value });
        },
        deleteTodoItem: function (itemIndex) {
            this.todoListItems.splice(itemIndex, 1);
        },
        editTodoItemTitle: function (info) {
            this.todoListItems[info.index].todoItemTitle = info.newTitle;
        },
    },
    data: () => {
        return {
            todoListItems: [
                { todoItemTitle: "Reading Comics" },
                { todoItemTitle: "Write Notes" },
            ],
        };
    },
};
</script>

<template>
    <div class="main_container">
        <div class="todo_list_title">Todo List</div>
        <Card
            v-for="(todoItem, index) in todoListItems"
            :todoItemTitle="todoItem.todoItemTitle"
            :key="index"
            :uniqueKey="index"
            v-on:deleteTodoItem="deleteTodoItem"
            v-on:editTodoItemTitle="editTodoItemTitle"
        />
        <input
            type="text"
            class="input-container"
            v-on:keyup="handleTodoItem"
            placeholder="Add a Item...."
        />
    </div>
</template>

<style>
.main_container {
    width: 800px;
    height: 800px;
    background: #05445e;
    border-radius: 4px;
}

input {
    border: none;
    outline: none;
    background-color: transparent;
    font-size: 16px;
    padding: 10px;
    margin: 0 12px;
}

.input-container {
    display: flex;
    align-items: center;
    background-color: #f0f0f0;
    border-radius: 8px;
    padding: 10px;
}

.todo_list_title {
    font-size: 28px;
    font-weight: 700;
    width: 100%;
    text-align: center;
    color: white;
    margin: 18px 0px;
}
</style>

/* Various Life Cycle Methods Mounted Unmounted updated created */
/*beforeCreate,created,mounted,beforeMount,beforeUpdated,updated */

<template>
    <div class="main_card_section">
        <div
            v-if="
                editButtonStatus.index != uniqueKey && !editButtonStatus.clicked
            "
            class="title-section"
        >
            {{ todoItemTitle }}
        </div>
        <div v-else class="title-section">
            <input
                type="text"
                class="container"
                @blur="setNewTitle"
                v-on:keydown.enter="setNewTitle"
                :value="editButtonStatus.editTitle"
            />
        </div>
        <div class="icons-section">
            <div class="edit-icon icons" @click="editItem">
                <i class="fa-solid fa-pen-to-square"></i>
            </div>
            <div class="delete-icon icons" v-on:click="deleteItem">
                <i class="fa-sharp fa-solid fa-trash"></i>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Card",
    data: function () {
        return {
            editButtonStatus: {
                clicked: false,
                index: null,
            },
        };
    },
    props: ["todoItemTitle", "uniqueKey"],
    methods: {
        deleteItem: function () {
            this.$emit("deleteTodoItem", this.uniqueKey);
        },
        editItem: function () {
            this.editButtonStatus = {
                ...this.editButtonStatus,
                clicked: true,
                index: this.uniqueKey,
                editTitle: this.todoItemTitle,
            };
        },
        setNewTitle: function (event) {
            this.editButtonStatus = { clicked: false, index: null };
            this.$emit("editTodoItemTitle", {
                newTitle: event.target.value,
                index: this.uniqueKey,
            });
        },
    },
};
</script>

<style>
.main_card_section {
    margin: 12px;
    padding: 10px;
    background: #75e6da;
    align-items: center;
    border-radius: 4px;
    font-weight: 700;
    display: flex;
    flex-direction: row;
}

.main_card_section:hover {
    cursor: pointer;
    background-color: #ddf8f5;
}

.icons-section {
    display: flex;
    flex-direction: row;
    margin-left: 10px;
}

.title-section {
    flex-grow: 1;
}

.edit-icon {
    margin-right: 16px;
}

.icons {
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.icons:hover {
    background: yellow;
    border-radius: 50%;
}

.container {
    background: #c0c2c9;
    border-radius: 8px;
    margin-right: 0;
    margin-left: 0px;
}
</style>

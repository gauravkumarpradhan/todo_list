<template>
    <h2 @click="changeName(newName)">{{ name }}</h2>
    <div>
        <h2>{{ count }}</h2>
        <div>
            <button @click="() => increment()">Increment</button>
            <button @click="() => decrement()">Dncrement</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "Learning",
    data: function () {
        return {
            name: "Gaurav Kumar Pradhan",
            newName: "Bat",
            count: 0,
        };
    },
    methods: {
        changeName: function (newName) {
            this.name = newName;
        },
        increment: function () {
            this.count += 1;
        },
        decrement: function () {
            this.count -= 1;
        },
    },
};
</script>

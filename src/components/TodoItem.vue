<template>
    <li>
        <input type="checkbox" v-model="item.isDone">
        <span :class="{'done':item.isDone}">{{ item.content }}</span>
        <span class="text-red" @click="removeTodo">x</span>
    </li>
</template>

<script>
export default {
    props: {
        item: Object,
    },
    methods: {
        removeTodo() {
            this.$emit('removeTodo')
        }
    }
}
</script>

<style scoped>
.text-red {
    cursor: pointer;
    color: red;
    font-weight: bold;
    margin-left: 10px;
}

.done {
    text-decoration: line-through;
}
</style>
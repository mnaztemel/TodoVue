<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['addTodo',])

const onAddTodo = (e) => {
    emit('addTodo', e.target.value)
    e.target.value = ''
}

</script>

<template>
    <div class="todo">
        <h1>Todos</h1>
        <input type="text" @keydown.enter="onAddTodo" />
        <hr />
    </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

interface TaskItem {
    name: string
    isCompleted: boolean
}

const taskItems = ref<TaskItem[]>([
    { name: '化学実験', isCompleted: false }, 
    { name: '物理学演習', isCompleted: true }
])
const newTaskItemName = ref('')

const addTaskItem = () => {
    if(newTaskItemName.value === '') {
        return
    }
    taskItems.value.push({ name: newTaskItemName.value, isCompleted: false })
    newTaskItemName.value = ''
}
</script>

<template>
    <div>
        <h4>NOT YET</h4>
        <ul>
            <template v-for="(taskItem, index) in taskItems" :key="taskItem.name">
                <li v-if="!taskItem.isCompleted">
                    <div>タスク: {{ taskItem.name }}</div>
                    <div>ステータス: {{ taskItem.isCompleted }}</div>
                    <label>
                        完了したか？
                        <input v-model="taskItems[index].isCompleted" type="checkbox" />
                    </label>
                </li>
            </template>
        </ul>
    </div>
    <div>
        <h4>COMPLETED</h4>
        <ul>
            <template v-for="(taskItem, index) in taskItems" :key="taskItem.name">
                <li v-if="taskItem.isCompleted">
                    <div>タスク: {{ taskItem.name }}</div>
                    <div>ステータス: {{ taskItem.isCompleted }}</div>
                    <label>
                        完了したか？
                        <input v-model="taskItems[index].isCompleted" type="checkbox" />
                    </label>
                </li>
            </template>
        </ul>
    </div>
    
    <div>
        <label>
            新規タスク
            <input v-model="newTaskItemName" type="text" />
        </label>
        <button @click="addTaskItem">追加</button>
    </div>

</template>

<style></style>
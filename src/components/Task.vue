<template>
    <div class="task" :class="stateClass">
        <span @click="$emit('taskDeleted', task)" class="close">x</span>
        <p>{{ task.name }}</p>
    </div>
</template>

<script>
export default {
    props: {
        task: {
            type: Object,
            required: true,
        },
    },
    computed: {
        stateClass() {
            return {
                pending: this.task.pending,
                done: !this.task.pending,
            };
        },
    },
};
</script>

<style>
.task {
    position: relative;
    box-sizing: border-box;
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2em;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
}

.pending {
    border-left: 12px solid #b73229;
    background-color: #f4433f;
}

.done {
    color: #ddd;
    border-left: 12px solid #0a8f08;
    background-color: #4caf50;
    text-decoration: line-through;
}

.pending .close {
    background-color: #b73229;
}

.done .close {
    background-color: #0a8f08;
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

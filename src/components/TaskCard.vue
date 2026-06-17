<script setup>
    import BaseCard from './BaseCard.vue';

    const props = defineProps({
        task: Object
    })

    const emit = defineEmits([
        'delete-task'
    ])

    const onDelete = () => {
        emit('delete', props.task.id);
    };

</script>
<template>
    <div>
        <BaseCard>
            <div class="text">
                <h1>{{ task.title }}</h1>
                <div class="status_completed">
                    <div class="status">STATUS:</div>

                    <div>
                                <div v-if="task.completed == true" class="true">
                                    completed</div>

                                <div v-else class="false"> Pending</div>
                    </div>
                        <button @click="onDelete">
                            Delete
                        </button>
                </div>
            </div>
        
        </BaseCard>
    </div>
</template>


<style scoped>
h1{
    font-size: 1.6rem;
    font-weight: 600;
    margin-bottom: 0.25rem;

}
.status_completed{
    display: flex;
    justify-content: space-between;
}

button{
    background: blue;
    border-radius: 10px;
    border: solid white;
    padding: 10px;
    color: white;
}

.status{
    color: blue;
    font-weight: bolder;
}
.true{
    color: rgb(165, 224, 165);
    background-color: green;
    padding: 5px;
    border-radius: 10px;

}
.false{
    color: rgb(191, 5, 5);
    background-color:rgb(239, 140, 140);
    padding: 5px;
    border-radius: 10px;
}
</style>
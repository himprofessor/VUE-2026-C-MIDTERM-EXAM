<template>
    <BaseCard :class="task.completed ? 'card-complete' : 'card-pending'">
        <div class="task-content">
            <h2 :class="{'text-done': task.completed}">{{ task.title }}</h2>

            <p class="status">
                Status: 
                <span :class="task.completed ? 'status-complete' : 'status-pending'">
                ● {{ task.completed ? 'Complete' : 'Pending' }}
                </span>
            </p>


            <div class="actions">
                <button 
                @click="$emit('status', task.id)" 
                class="btn-action"
                >
                {{ task.completed ? 'Undo' : 'Complete' }}
                </button>
                
                <button @click="$emit('delete', task.id)" class="btn-delete">
                Delete
                </button>
            </div>


        </div>

    </BaseCard>
</template>

<script setup>
    import BaseCard from './BaseCard.vue';

    defineProps ({
        task : {
            type: Object,
            required: true
        }
    });
    defineEmits (['status', 'delete'])

</script>

<style>
    h3 { 
        margin: 0 0 0.5rem 0; 
        color: #2c3e50; 
    }
    .text-done { 
        text-decoration: line-through; 
        color: #95a5a6; 
    }
    .done-tag { 
        margin: 0 0 0.5rem 0; 
        color: #27ae60; 
        font-size: 0.9rem; 
    }

    .card-complete { 
        border-left-color: #27ae60 !important; 
    }
    .card-pending { 
        border-left-color: #e67e22 !important; 
    }

    .status { 
        margin: 0.5rem 0; 
        font-size: 0.95rem; 
    }
    .status-complete { 
        color: #27ae60; 
        font-weight: bold; 
    }
    .status-pending { 
        color: #e67e22; 
        font-weight: bold; 
    }

    .actions { 
        margin-top: 1rem; 
        display: flex; 
        gap: 0.5rem; }
    button { 
        padding: 0.4rem 0.8rem; 
        border: 1px solid #ccc; 
        border-radius: 4px; 
        background: #fff; 
        cursor: pointer; 
        font-size: 0.9rem;
    }
    button:hover { 
        background: #f0f0f0; 
    }
    .btn-delete { 
        color: #c0392b; 
        border-color: #d98880; 
    }
    .btn-delete:hover { 
        background: #fadbd8; 
        }
</style>
<template>
    <div>
        <v-list-item @click="$store.commit('doneTask', task.id)" :class="{ 'blue lighten-5' : task.done }">
            <template v-slot:default>
                <v-list-item-action>
                    <v-checkbox :input-value="task.done" color="primary"></v-checkbox>
                </v-list-item-action>

                <v-list-item-content>
                    <v-list-item-title :class="{ 'text-decoration-line-through' : task.done }">
                        {{task.title}}</v-list-item-title>
                </v-list-item-content>
                <v-list-item-icon>
                    <task-menu :task="task" />                   
                </v-list-item-icon>
            </template>
        </v-list-item>
        <v-divider></v-divider>

    </div>
</template>

<script>
export default {
    name: 'VueTodoTask',
    props: ['task'],  
    components: {  
        'task-menu': require('@/components/Todo/TaskMenu.vue').default
    }
};
</script>
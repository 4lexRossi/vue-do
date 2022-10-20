<template>
    <div>
        <v-list-item
          :class="{ 'blue lighten-5' : task.done }"
          @click="$store.commit('doneTask', task.id)"
        >
            <template v-slot:default>
                <v-list-item-action>
                    <v-checkbox :input-value="task.done" color="primary"></v-checkbox>
                </v-list-item-action>

                <v-list-item-content>
                    <v-list-item-title
                      :class="{ 'text-decoration-line-through' : task.done }"
                    >
                        {{task.title}}</v-list-item-title>
                </v-list-item-content>
                <v-list-item-action v-if="task.dueDate">
                    <v-list-item-action-text>
                        <v-icon small>mdi-calendar</v-icon>
                        {{ task.dueDate | formatedDate }}
                    </v-list-item-action-text>
                </v-list-item-action>

                <v-list-item-icon>
                    <task-menu :task="task" />                   
                </v-list-item-icon>
            </template>
        </v-list-item>
        <v-divider></v-divider>

    </div>
</template>

<script>
import { format } from 'date-fns';

export default {
    name: 'VueTodoTask',
    props: ['task'],  
    
    filters: {
        formatedDate(value) {
            value = value.replaceAll('-', '/')
            return format(new Date(value), 'd MMM')
        }
    },

    components: {  
        'task-menu': require('@/components/Todo/TaskMenu.vue').default
    }
};
</script>
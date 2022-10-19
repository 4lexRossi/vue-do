<template>
    <v-text-field
      v-model="newTaskTitle"
      @keyup.enter="addTask"
      class="pa-3"
      label="Add a Task"
      clearable
      hide-details
      solo
    >
        <template v-slot:append>
            <v-fade-transition leave-absolute>
               <v-icon
                @click="addTask"     
                color="primary"           
                :disabled="isNewTaskTitleInvalid"
               >
                    mdi-plus
               </v-icon>
            </v-fade-transition>
        </template>
    </v-text-field>
</template>

<script>
export default {
    name: 'VueTodoFieldAddTask',

    data() {
        return {
            newTaskTitle: ''
        }
    },
    
    computed: {
        isNewTaskTitleInvalid() {
            return !this.newTaskTitle
        }
    },

    methods: {
        addTask() {
            if(!this.isNewTaskTitleInvalid) {
                this.$store.dispatch('addTask', this.newTaskTitle)
                this.newTaskTitle = ''
            }
        },        
    },
};
</script>
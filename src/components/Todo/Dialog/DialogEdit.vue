<template>
    <v-dialog
      :value="true"
      persistent
      max-width="290"
    >      
      <v-card>
        <v-card-title class="text-h5">
          Edit task?
        </v-card-title>
        <v-card-text>
          Edit the title of this Task?
          <v-text-field
            v-model="taskTitle"
            @keyup.enter="saveTask"
          />
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click="$emit('close')"
          >
            Cancel
          </v-btn>
          <v-btn
            :disabled="isTaskTitleInvalid"
            color="blue darken-1"
            text
            @click="saveTask"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>

<script>
export default {
    name: 'VueTodoDialogDelete',
    props:['task'],
    data() {
        return {
            taskTitle: null
        };
    },
    
    computed: {
      isTaskTitleInvalid() {
        return !this.taskTitle || this.taskTitle === this.task.title
      }
    },
    
    methods: {
      saveTask() {
        if(!this.isTaskTitleInvalid) {
          const payload = {
            id: this.task.id,
            title: this.taskTitle
          }
          this.$store.dispatch('updateTaskTitle', payload)
          this.$emit('close')
        }
      }
    },

    mounted() {
        this.taskTitle = this.task.title
    },
};
</script>

<style lang="scss" scoped>

</style>
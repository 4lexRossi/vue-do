<template>
    <v-dialog
      :value="true"
      persistent
      max-width="290"
    >      
      <v-card>
        <v-card-title class="text-h5">
          Delete task?
        </v-card-title>
        <v-card-text>Sure want to delete Task?</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            text
            @click="$emit('close')"
          >
            Cancel
          </v-btn>
          <v-btn
            color="red darken-1"
            text
            @click="$store.dispatch('deleteTask', task.id)"
          >
            Delete
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
            
        };
    },

    mounted() {
        
    },

    methods: {
        
    },
};
</script>

<style lang="scss" scoped>

</style>
<template>
    <div class="text-subtitle-1 ml-4">
        {{ date }}
    </div>
</template>

<script>
import { format } from 'date-fns';

export default {
    name: 'VueTodoLiveDateTime',

    data() {
        return {
            date: ''
        };
    },

    mounted() {
        this.getDate()
    },

    methods: {
        getDate() {
            this.date = format(new Date(), 'd MMMM, H:mm:ss')
            setTimeout(this.getDate, 1000);
        }
    },
};
</script>
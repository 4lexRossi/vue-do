<template>
    <v-btn
        @click="$store.commit('toggleSorting')"
        class="done-sorting"
        color="primary"
    >
        Done Sorting
    </v-btn>
</template>

<script>
export default {
    name: 'VueTodoDoneSortingButton',
};
</script>
<style lang="sass">
    .done-sorting
        position: fixed
        bottom: 20px
        left: 50%
        transform: translateX(-50%)
</style>
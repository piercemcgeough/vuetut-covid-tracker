<template>
    <h1 class="text-center text-3xl font-bold mb-3">{{ title }}</h1>
    <p class="text-center mb-3">{{ dateForHuman }}</p>
</template>

<script>
import moment from 'moment'

export default {
    name: 'DataTitle',

    props: {
        title: String,
        date: String
    },

    computed: {
        dateForHuman: function () {
            return moment(this.date).format('ddd Do MMMM YYYY (H:mm)')
        }
    }
}
</script>

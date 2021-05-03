<template>
    <div class="shadow-md p-10 text-center rounded" :class="backgroundColour">
        <h3 class="text-3xl text-purple-900 font-bold mb-4">{{ title }}</h3>

        <div class="text-2xl mb-4">
            <span class="font-bold">New: </span>
            {{ numberWithCommas(newNumbers) }}
        </div>

        <div class="text-2xl mb-4">
            <span class="font-bold">Total: </span>
            {{ numberWithCommas(totalNumbers) }}
        </div>
    </div>
</template>

<script>
export default {
    name: 'DataBox',

    props: {
        title: String,
        newNumbers: Number,
        totalNumbers: Number,
        backgroundColour: String
    },

    methods: {
        numberWithCommas(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
        }
    },
}
</script>

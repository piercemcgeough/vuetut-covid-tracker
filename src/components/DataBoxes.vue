<template>
    <div class="grid md:grid-cols-2 gap-8 mb-10">
        <DataBox
            :backgroundColour="`bg-purple-100`"
            :title="`Cases`"
            :newNumbers='stats.NewConfirmed'
            :totalNumbers='stats.TotalConfirmed'
        />

        <DataBox
            :backgroundColour="`bg-purple-200`"
            :title="`Deaths`"
            :newNumbers='stats.NewDeaths'
            :totalNumbers='stats.TotalDeaths'
        />
    </div>
</template>

<script>
import DataBox from '@/components/DataBox'

export default {
    name: 'DataBoxes',

    props: {
        stats: Object
    },

    components: {
        DataBox
    },
}
</script>

<template>
    <div v-if="!loading">
        <DataTitle
            :title="title"
            :date="dataDate"
        />

        <DataBoxes
            :stats="stats"
        />

        <CountrySelect
            :countries="countries"
            @get-country="getCountryData"
            @clear-selection="clearSelection"
        />

        <button
            type="button"
            class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green900"
            v-show="stats.Country"
            @click="clearSelection"
        >
            Clear Selection
        </button>
    </div>

    <Loading v-else />
</template>

<script>
import Loading from '@/components/Loading'
import DataBoxes from '@/components/DataBoxes'
import DataTitle from '@/components/DataTitle'
import CountrySelect from '@/components/CountrySelect'

export default {
    name: 'Home',

    components: {
        Loading,
        DataBoxes,
        DataTitle,
        CountrySelect
    },

    data() {
        return {
            loading: true,
            title: 'Global',
            dataDate: '',
            stats: [],
            countries: {},
        }
    },

    methods: {
        getCountryData(countryId) {
            this.loading = true

            const country = this.countries.find(country => country.ID == countryId)

            this.stats = country
            this.title = country.Country
            this.dataDate = country.Date

            this.loading = false
        },

        async getCovidData() {
            const res = await fetch('https://api.covid19api.com/summary')

            return await res.json()
        },

        async clearSelection() {
            this.loading = true

            await this.setDefaults()

            this.loading = false
        },

        async setDefaults() {
            const data = await this.getCovidData()

            this.title = 'Global'
            this.dataDate = data.Date
            this.stats = data.Global
            this.countries = data.Countries
        }
    },

    async created() {
        await this.setDefaults()

        this.loading = false
    }
}
</script>

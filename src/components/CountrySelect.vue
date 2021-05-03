<template>
    <select
        class="form-select block w-full border p-3 rounded"
        v-model="selectedCountry"
        @change="getCountryData"
    >
        <option value="0">Select a country...</option>

        <option
            v-for="country in countries"
            :key="country.ID"
            :value="country.ID"
        >
            {{ country.Country }}
        </option>
    </select>
</template>

<script>
export default {
    name: 'CountrySelect',

    props: {
        countries: Object
    },

    data() {
        return {
            selectedCountry: 0
        }
    },

    methods: {
        getCountryData() {
            if (this.selectedCountry == 0) {
                this.$emit('clear-selection')
            } else {
                this.$emit('get-country', this.selectedCountry)
            }
        }
    }
}
</script>

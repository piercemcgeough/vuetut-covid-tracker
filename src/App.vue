<template>
    <Header />

    <div class="container mx-auto">
        <router-view/>
    </div>
</template>

<script>
import Header from '@/components/Header.vue'

export default {
    name: 'App',

    components: {
        Header
    }
}
</script>

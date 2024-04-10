<script>
    import Navbar from '@/components/Navbar.vue'
    export default {
        name: 'MainLayout',
        components: {
            Navbar
        }
    }
</script>
<template>
    <div>
        <Navbar />
        <slot></slot>
    </div>
</template>


<template>
    <div class="dashboard v-2">
        <DashboardNotify/>
        <DashboardFilter/>
        <DashboardTab/>
    </div>
</template>

<script>
    import DashboardNotify from './DashboardNotify.vue';
    import DashboardFilter from './DashboardFilter.vue';
    import DashboardTab from './DashboardTab.vue';

    export default {
        name: 'Dashboard',
        components: {
            "DashboardNotify": DashboardNotify,
            "DashboardFilter": DashboardFilter,
            "DashboardTab": DashboardTab
        },
        data() {
            return {
            }
        },
    }
</script>

<style lang="sass">
    @import './sass/Dashboard.sass'
</style>

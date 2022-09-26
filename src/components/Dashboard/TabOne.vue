<template>
    <div 
        class="dashboard-tab-body-content"
        :class="{ 'active': isActive}"
    >
        <DashboardKey/>
        <div class="dashboard-card">
            <DashboardCard/>
            <DashboardCard/>
            <DashboardCard/>
        </div>
    </div>
</template>

<script>
    import DashboardCard from './DashboardCard.vue';
    import DashboardKey from './DashboardKey.vue';

    export default {
        name: "TabOne",
        components: {
            'DashboardKey': DashboardKey,
            'DashboardCard': DashboardCard
        },
        props: {
            isActive: Boolean,
            heading: Number,
            onTabHeadingSPClick: Function
        },
        data() {
            return {
                
            };
        },
        
    }
</script>

<style lang="css" scoped>
</style>

<template>
    <div 
        class="dashboard-tab-body-content"
        :class="{ 'active': isActive}"
    >
        <div class="dashboard-uncompleted-card">
            <DashboardUncompletedCard/>
            <DashboardUncompletedCard/>
            <DashboardUncompletedCard/>
        </div>
    </div>
</template>

<script>
import DashboardUncompletedCard from './DashboardUncompletedCard.vue';

export default {
    name: 'TabThree',
    components: {
        "DashboardUncompletedCard": DashboardUncompletedCard,
    },
    props: {
        isActive: Boolean,
    },
    data() {
        return {}
    },
}
</script>

<style lang="css" scoped>

</style>

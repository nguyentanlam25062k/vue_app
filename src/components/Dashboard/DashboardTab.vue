<template>
    <div class="dashboard-tab v-2">
        <ul class="db-heading-pc">
            <TabHeading 
                v-for="{ index } in tabs" 
                :index="index" 
                :isActive="index === currentTab" 
                :onTabHeadingClick="TabHeadingClick" 
            />
        </ul>
        <ul class="db-body">
            <li class="db-body-item" 
                v-for="{ index, content } in tabs"
            >
                <TabHeadingSP 
                    :index="index" 
                    :isActive="index === currentTab" 
                    :onTabHeadingSPClick="TabHeadingSPClick" 
                />
                <component
                    :is="content"
                    :isActive="index === currentTab"
                />
            </li>
        </ul>
    </div>
</template>

<script>
    import TabHeading from './TabHeading.vue';
    import TabHeadingSP from './TabHeadingSP.vue';
    import TabOne from './TabOne.vue';
    import TabTwo from './TabTwo.vue';
    import TabThree from './TabThree.vue';

    const TAB_DEFAULT = 1;

    export default {
        name: 'DashboardTab',
        components: {
            'TabHeading': TabHeading,
            'TabHeadingSP': TabHeadingSP,
            "TabOne": TabOne,
            "TabTwo": TabTwo,
            "TabThree": TabThree,
        },
        data() {
            return {
                currentTab: TAB_DEFAULT,
                tabs: [
                    { index: 1, heading: 1, content: TabOne },
                    { index: 2, heading: 2, content: TabTwo },
                    { index: 3, heading: 3, content: TabThree },
                ]
            }
        },
        methods: {
            TabHeadingClick(index) {
                this.currentTab = index;
            },
            TabHeadingSPClick(index) {
                if(this.currentTab === index) {
                    this.currentTab = null;
                    return;
                }
                this.currentTab = index;
            },
        },
    }
</script>

<style lang="css" scoped>
</style>
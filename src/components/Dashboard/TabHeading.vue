<template>
    <li class="dashboard-tab-heading-item"
         :class="{active: isActive}"
         @click="() => { onTabHeadingClick(index) }"
    >
        <div class="box-blue">
            <div class="box-blue-row">
                <div class="box-blue-col">
                    <div class="text-small">内見予定</div>
                    <div class="text-big">本日</div>
                </div>
                <div class="box-blue-col">
                    <div class="number-big">1</div>
                    <div class="number-small">件</div>
                </div>
            </div>
            <div class="box-blue-icon">
                <span class="material-icons">info</span>
                <!-- <span class="icon-notice"></span> -->
            </div>
        </div>
        <div class="infor">
            <div class="infor-heading">未登録の事前準備タスク</div>
            <div class="infor-list">
                <div class="infor-item">
                    <div class="infor-item-text">物件情報</div>
                    <div class="infor-item-number">1<span>件</span></div>
                </div>
                <div class="infor-item disable">
                    <div class="infor-item-text">物件情報</div>
                    <div class="infor-item-number">1<span>件</span></div>
                </div>
                <div class="infor-item disable">
                    <div class="infor-item-text">物件情報</div>
                    <div class="infor-item-number">1<span>件</span></div>
                </div>
            </div>
        </div>
    </li>
</template>
<script>
export default {
    name: 'TabHeading',
    props: {
        index: Number,
        isActive: Boolean,
        onTabHeadingClick: Function
    },
    data() {
        return {}
    },
    methods: {}
}
</script>
<style lang="css" scoped>
</style>
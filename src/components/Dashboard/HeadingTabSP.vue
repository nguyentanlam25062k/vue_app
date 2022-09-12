<template>
<div class="db-tab-heading-sp">
    <div class="db-tab-heading-sp-row">
        <div class="db-box-blue">
            <div class="db-box-blue-row">
                <div class="db-box-blue-col">
                    <div class="db-text-small">内見予定</div>
                    <div class="db-text-big">本日</div>
                </div>
                <div class="db-box-blue-col">
                    <div class="db-number-big">1</div>
                    <div class="db-number-small">件</div>
                </div>
            </div>
            <div class="db-box-blue-icon">
                <span class="icon-notice"></span>
            </div>
        </div>
        <div class="db-info">
            <div class="db-info-heading">未登録の事前準備タスク</div>
            <div class="db-info-list">
                <div class="db-info-item">
                    <div class="db-info-item-text">物件情報</div>
                    <div class="db-info-item-number">1<span>件</span></div>
                </div>
                <div class="db-info-item disable">
                    <div class="db-info-item-text">物件情報</div>
                    <div class="db-info-item-number">1<span>件</span></div>
                </div>
                <div class="db-info-item disable">
                    <div class="db-info-item-text">物件情報</div>
                    <div class="db-info-item-number">1<span>件</span></div>
                </div>
            </div>
        </div>
    </div>
    <div class="db-arrow"
        :class="{active: isActive}"
    >
        <span class="icon v-2 icon-arrow-right" 
            @click="() => {onHeadingTabSPClick(heading)}"
        >></span>
    </div>
</div>
</template>

    
<script>
export default {
    name: 'HeadingTabItemSP',
    props: {
        heading: Number,
        isActive: Boolean,
        onHeadingTabSPClick: Function
    },
    data() {
        return {
            
        }
    }
}
</script>
    
<style lang="css" scoped>
</style>

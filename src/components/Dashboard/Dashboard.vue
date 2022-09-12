<template>
<div class="dashboard v-2">
    <div class="dashboard-notify v-2">
        <div class="db-notify-heading">お知らせ</div>
        <div class="db-notify-slide">
            <ul class="db-notify-list"
                :style="{top: -currentSlide*slideItemHeight + 'px'}"
            >
                <li class="db-notify-item"
                    v-for="slide in slides"
                >
                    <div class="db-notify-item-time">yyyy.mm.dd</div>
                    <a class="db-notify-item-link" href="#">{{ slide }}</a>
                    <div class="db-notify-item-icon">
                        <span class="icon-external">open</span>
                    </div>
                </li>
            </ul>
        </div>
        <div class="db-notify-close">
            <span class="icon-close-cl-ol">close</span>
        </div>
    </div>
    <div class="dashboard-manager v-2">
        <div class="db-manager-text">担当者</div>
        <div class="db-manager-select">
            <select name="" id="" class="">
                <option class="db-manager-select" value="">1</option>
                <option class="db-manager-select" value="">2</option>
                <option class="db-manager-select" value="">3</option>
            </select>
        </div>
       
    </div>   
    <div class="dashboard-tab v-2">
        <ul class="db-tab-heading-pc">
            <HeadingTab 
                v-for="tab in tabs" 
                :heading="tab.heading" 
                :isActive="tab.heading === currentTab" 
                :onHeadingTabClick="handleHeadingTabClick" 
            />
        </ul>
        <ul class="db-tab-body">
            <li class="db-tab-body-item" 
                v-for="tab in tabs"
            >
                <!-- <h1>tab {{ tab.heading}}</h1> -->
                <HeadingTabSP 
                    :heading="tab.heading" 
                    :isActive="tab.heading === currentTab" 
                    :onHeadingTabSPClick="handleHeadingTabSPClick" 
                />
                <component
                    v-if="tab.heading === currentTab" 
                    :is="tab.content"
                />
            </li>
        </ul>
    </div>
</div>
</template>

<script>
import HeadingTab from './HeadingTab.vue';
import HeadingTabSP from './HeadingTabSP.vue';
import ContentTab from './ContentTab.vue';
import TabOne from './TabOne.vue';
import TabTwo from './TabTwo.vue';
import TabThree from './TabThree.vue';

const SLIDE_DEFAULT = 0;
const TAB_DEFAULT = 1;
const SLIDE_SPEED = 2000;
const SLIDE_ITEM_HEIGHT = 28;

export default {
    name: 'Dashboard',
    components: {
        'HeadingTab': HeadingTab,
        'HeadingTabSP': HeadingTabSP,
        'ContentTab': ContentTab,
        'TabOne': TabOne,
        'TabTwo': TabTwo,
        'TabThree': TabThree
    },
    data() {
        return {
            currentSlide: SLIDE_DEFAULT,
            currentTab: TAB_DEFAULT,
            timer: null,
            slideItemHeight: SLIDE_ITEM_HEIGHT,
            slides: [
                'Lorem ipsum dolor sit amet consectetur adipisicing elit 1',
                'Lorem ipsum dolor sit amet consectetur adipisicing elit 2',
                'Lorem ipsum dolor sit amet consectetur adipisicing elit 3',
                'Lorem ipsum dolor sit amet consectetur adipisicing elit 4',
                'Lorem ipsum dolor sit amet consectetur adipisicing elit 5',
            ],
            tabs: [
                { heading: 1, content: TabOne },
                { heading: 2, content: TabTwo },
                { heading: 3, content: TabThree },
            ]
        }
    },
    created() {
        this.playSlide();
    },
    mounted() {
        const itemHeight = document.querySelector('.db-notify-item').offsetHeight || SLIDE_ITEM_HEIGHT;
        this.slideItemHeight = itemHeight;
    },
    methods: {
        nextSlide() {
            this.currentSlide++;
            if(this.currentSlide > this.slides.length) {
                this.currentSlide = SLIDE_DEFAULT;
            }
            this.resetPlay();
        },
        playSlide() {
            this.timer = setInterval(() => {
                this.nextSlide();
            }, SLIDE_SPEED);

        },
        resetPlay() {
            clearInterval(this.timer);
            this.playSlide();
        },

        handleHeadingTabClick(tabSelected) {
            this.currentTab = tabSelected;
        },
        handleHeadingTabSPClick(tabSelected) {
            if(this.currentTab === tabSelected) {
                this.currentTab = null;
                return;
            }
            this.currentTab = tabSelected;
        },
    },

}
</script>

<style lang="sass">
@import './Dashboard.sass'
</style>

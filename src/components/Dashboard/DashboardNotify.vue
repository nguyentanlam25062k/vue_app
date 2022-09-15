<template>
    <div class="dashboard-notify v-2">
        <div class="db-heading">お知らせ</div>
        <div class="db-slide">
            <ul class="db-list"
                :style="{top: -currentSlide*slideItemHeight + 'px'}"
            >
                <li class="db-item"
                    v-for="slide in slides"
                >
                    <div class="db-item-time">yyyy.mm.dd</div>
                    <a class="db-item-link" href="#">{{ slide }}</a>
                    <div class="db-item-icon">
                        <span class="material-icons">logout</span>
                        <!-- <span class="icon-external"></span> -->
                    </div>
                </li>
            </ul>
        </div>
        <div class="db-close">
            <v-icon>cancel</v-icon>
            <!-- <span class="icon-close-cl-ol">close</span> -->
        </div>
    </div>
</template>

<script>
    const SLIDE_DEFAULT = 0;
    const SLIDE_SPEED = 2000;
    const SLIDE_ITEM_HEIGHT = 28;

    export default {
        name: 'DashboardNotify',
        data() {
            return {
                timer: null,
                currentSlide: SLIDE_DEFAULT,
                slideItemHeight: SLIDE_ITEM_HEIGHT,
                slides: [
                    'Lorem ipsum dolor sit amet consectetur adipisicing elit 1',
                    'Lorem ipsum dolor sit amet consectetur adipisicing elit 2',
                    'Lorem ipsum dolor sit amet consectetur adipisicing elit 3',
                    'Lorem ipsum dolor sit amet consectetur adipisicing elit 4',
                    'Lorem ipsum dolor sit amet consectetur adipisicing elit 5',
                ],
            }
        },
        created() {
            this.playSlide();
        },
        mounted() {
            const itemHeight = document.querySelector('.dashboard-notify.v-2 .db-item').offsetHeight || SLIDE_ITEM_HEIGHT;
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
        }
        
    }
</script>
<style lang="css" scoped>
</style>
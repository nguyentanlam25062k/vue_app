<template>
    <div class="dashboard-notify">
        <div class="heading">お知らせ</div>
        <div class="slide">
            <ul class="list"
                ref="slideListRef"
                :style="{ transform: `translateY(-${translateY}px)` }"
            >
                <li class="item"
                    ref="slideItemRef"
                    v-for="slide in slides"
                >
                    <div class="item-time">yyyy.mm.dd</div>
                    <a class="item-link" href="#">{{ slide }}</a>
                    <div class="item-icon">
                        <span class="material-icons">logout</span>
                        <!-- <span class="icon-external"></span> -->
                    </div>
                </li>
            </ul>
        </div>
        <!-- <h1 @click="nextSlide">next</h1> -->
        <div class="close">
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
                translateY: SLIDE_ITEM_HEIGHT,
                leng: 0,
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
            this.leng = this.slides.length;
            this.initNewSlides();
            this.playSlide();
        },
        mounted() {
            const itemHeight = this.$refs.slideItemRef.offsetHeight || SLIDE_ITEM_HEIGHT;
            this.slideItemHeight = itemHeight;
        },
        methods: {
            initNewSlides() {
                const firstSlideClone = this.slides[0];
                const secondSlideClone = this.slides[1];
                const lastSlideClone = this.slides[this.slides.length - 1];
                this.slides = [lastSlideClone, ...this.slides, firstSlideClone, secondSlideClone];
            },
            transitionend() {
                this.$refs.slideListRef.style.transitionDuration = "0ms";
                this.translateY = SLIDE_ITEM_HEIGHT;
                this.currentSlide = SLIDE_DEFAULT;
            },
            nextSlide() {
                this.currentSlide++;
                this.$refs.slideListRef.style.transitionDuration = "1000ms";
                this.$refs.slideListRef.removeEventListener('transitionend', this.transitionend);

                if(this.currentSlide > this.leng - 1) {
                    this.$refs.slideListRef.addEventListener('transitionend', this.transitionend);
                }
                
                this.translateY = this.slideItemHeight * (this.currentSlide + 1);
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
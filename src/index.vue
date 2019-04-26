<template>
    <div class="index">
        <div class="index__box">banner</div>
        <div class="index__box1">新闻</div>
        <div class="index__box2">条</div>
        <div class="index__box3"></div>
        <div class="index__box4">块</div>
    </div>
</template>

<script>
import { TweenMax, TimelineMax, Linear } from 'gsap/TweenMax'
export default {
    data() {
        return {
            time : 1
        }
    },

    computed: {

    },

    methods: {
        init() {
            this.timeline = new TimelineMax({
                paused: true
            });
            this.action = TweenMax.fromTo('.index__box3', 1, {
                x: 208,
                alpha: 0.12,
                ease: Linear.easeNone
            }, {
                x: -361,
                alpha: 1,
                ease: Linear.easeNone
            });

            this.timeline.add(this.action)

            // 绑定滚动事件
            window.addEventListener('scroll', this.onScroll.bind(this));
        },

        onScroll() {
            const totalHeight = window.innerHeight * 5; // 整个页面的总高度
            const scrollTop = window.scrollY; // 当前滚动高度
            const progress = scrollTop / (totalHeight - window.innerHeight); // 当前滚动进度
            console.log(progress)
            // this.timeline.seek(progress - 0.4);
            this.timeline.seek(progress);
        }
    },
    mounted() {
        this.init();
    }
}
</script>
<style lang="scss">
.index{
    width: 100vw;
    height: 272rem;
    position: relative;
    &__box{
        position: absolute;
        top: 0;
        left: 0;
        background-color: red;
        width: 100vw;
        height: 68rem;
        font-size: 34px;
        text-align: center;
    }
    &__box1{
        position: absolute;
        top: 68rem;
        left: 0;
        background-color: yellow;
        width: 100vw;
        height: 68rem;
        font-size: 34px;
        text-align: center;
    }
    &__box2{
        position: absolute;
        top: 128rem;
        left: 0;
        background-color: green;
        width: 100rem;
        height: 16rem;
        border-radius: 18rem;
        background-color: #cde9f7;
        z-index: 1;
        transform: translate(-50%,0);
    }
    &__box3{
        position: absolute;
        top: 136rem;
        left: 0;
        background-color: blue;
        width: 100vw;
        height: 136rem;
        border-top-left-radius: 20rem;
        border-bottom-right-radius: 20rem;
    }
    &__box4{
        position: absolute;
        top: 272rem;
        left: 0;
        background-color: green;
        width: 100vw;
        height: 68rem;
    }
}
</style>

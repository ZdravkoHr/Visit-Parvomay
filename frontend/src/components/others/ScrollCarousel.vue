<template>
    <div class="wrapper" ref="wrapper">
        <div
            class="content"
            ref="content"
            :style="contentStyles"
            @scroll="updateScrollValue($event)"
        >
            <div class="empty-box"></div>
            <slot name="items"></slot>
            <div class="empty-box"></div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["itemWidth"],

    data() {
        return {
            contentEl: null,
            items: null,
            scrollValue: 0,
            activeIndex: -1
        };
    },

    methods: {
        initVars() {
            this.contentEl = this.$refs.content;
            this.items = this.contentEl.children;
            this.activeIndex = 2;
            // this.activeIndex = Math.floor(this.items.length / 2);
        },
        updateScrollValue(event) {
            const scrollValue = event.target.scrollLeft;
            this.activeIndex = Math.floor(scrollValue / this.itemWidth) + 1;
        },
        scroll() {
            const scrollX = this.items[this.activeIndex].previousElementSibling
                .offsetLeft;

            setTimeout(() => this.contentEl.scroll(scrollX, 0));
        }
    },

    computed: {
        contentStyles() {
            const count = (this.items || []).length;
            return {
                gridTemplateColumns: `repeat(${count + 2}, ${this.itemWidth}px)`
            };
        },
        activeElement() {
            return this.items[this.activeIndex];
        }
    },

    mounted() {
        this.initVars();
        this.scroll();
        //  this.activeElement.style.transform = "scale(1)";
    },

    watch: {
        activeIndex(newValue) {
            this.items.forEach(item => item.classList.remove("active"));
            this.items[newValue].classList.add("active");
        }
        // scrollValue(newValue) {
        //     const percentsAway = Math.min(
        //         (newValue /
        //             (this.activeElement.offsetLeft -
        //                 (this.activeElement.previousElementSibling
        //                     ?.offsetLeft || 0))) *
        //             100,
        //         100
        //     );

        //     console.log(this.activeElement.previousElementSibling.offsetLeft);

        //     const scaleChange = (percentsAway / 100) * 0.4;
        //     const decreasedScale = 1 - scaleChange;
        //     const increasedScale = 0.6 + scaleChange;

        //     this.activeElement.style.transform = `scale(${decreasedScale})`;
        //     this.activeElement.nextElementSibling.style.transform = `scale(${increasedScale})`;

        //     if (percentsAway === 100) {
        //         this.activeIndex++;
        //     }
        // }
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;

.content {
    position: relative;
    display: grid;

    overflow-x: scroll;

    ::v-deep(.box) {
        position: relative;
        transition: 0.3s;
        &:not(.active) {
            transform: scale(0.6);

            &::before {
                content: "";
                @include overlay(0.4);
            }
        }
    }
}
</style>

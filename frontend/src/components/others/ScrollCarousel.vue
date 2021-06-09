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
            activeIndex: -1,
            lastBoxWidth: 160
        };
    },

    methods: {
        initVars() {
            this.contentEl = this.$refs.content;
            this.items = this.contentEl.children;
            this.activeIndex = this.items.length > 2 ? 2 : this.items.length;
        },
        updateScrollValue(event) {
            const scrollValue = event.target.scrollLeft;
            this.activeIndex = Math.floor(scrollValue / this.itemWidth) + 1;
        },
        scroll() {
            const scrollX = this.items[this.activeIndex].previousElementSibling
                .offsetLeft;

            setTimeout(() => this.contentEl.scroll(scrollX, 0));
        },
        addScrollWidth() {
            const additionalWidth = Math.max(
                (this.itemsCount - 2) * this.itemWidth -
                    this.contentEl.scrollLeftMax,
                0
            );

            this.lastBoxWidth = additionalWidth;
        }
    },

    computed: {
        contentStyles() {
            return {
                gridTemplateColumns: `repeat(${this.itemsCount - 1}, ${
                    this.itemWidth
                }px) ${this.lastBoxWidth}px`
            };
        },
        itemsCount() {
            return (this.items || []).length;
        },
        activeElement() {
            return this.items[this.activeIndex];
        }
    },

    mounted() {
        this.initVars();
        this.$nextTick(() => {
            this.addScrollWidth();
            this.scroll();
        });
    },

    watch: {
        activeIndex(newValue) {
            this.items.forEach(item => item.classList.remove("active"));
            this.items[newValue].classList.add("active");
        }
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;

.content {
    @include hidden-scroll;
    position: relative;
    display: grid;
    overflow-x: scroll;
    appearance: none;

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

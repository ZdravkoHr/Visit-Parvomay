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
            lastBoxWidth: 1
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


            if (scrollValue <= 20) {
                this.activeIndex = 1;
                return;
            }
        
            this.activeIndex = Math.floor(scrollValue / this.itemWidth) + 2;
        },

        scroll() {
            const scrollX = this.items[this.activeIndex].previousElementSibling
                .offsetLeft + 2;

            setTimeout(() => this.contentEl.scroll(scrollX, 0));
        },
        addScrollWidth() {
            const maxScroll =  this.contentEl.scrollWidth - this.contentEl.clientWidth;
            const lastElLeft = this.items[this.items.length - 2].offsetLeft;

            const additionalWidth = lastElLeft - (maxScroll + this.itemWidth);

     
         this.lastBoxWidth = Math.max(additionalWidth, 0);
        }
    },

    computed: {
        contentStyles() {
            return {
                gridTemplateColumns: `20px repeat(${this.itemsCount - 2}, ${
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
            user-select: none;

            @include mobile() {
                transform: scale(0.8);
            }

            &::before {
                content: "";
                @include overlay(0.4);
            }
        }
    }

   
}
</style>

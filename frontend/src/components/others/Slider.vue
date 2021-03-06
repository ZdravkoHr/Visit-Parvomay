<template>
    <div class="wrapper" ref="wrapper">
        <div class="content" ref="content">
            <div
                class="slider"
                ref="slider"
                :style="sliderStyles"
                @transitionend="arrangeItems"
            >
                <slot name="items"></slot>
            </div>
        </div>

        <div class="controls">
            <button @click="prev" class="btn">
                <i class="far fa-arrow-alt-circle-left "></i>
            </button>
            <button @click="next" class="btn">
                <i class="far fa-arrow-alt-circle-right  "></i>
            </button>
        </div>
    </div>
</template>

<script>
const NEXT = 1;
const PREV = -1;

export default {
    props: ["itemsCount", "itemWidth"],
    emits: ["arrangeItems"],

    data() {
        return {
            direction: NEXT,
            dontArrange: false
        };
    },

    computed: {
        sliderStyles() {
            return {
                width: this.itemsCount * 100 + "%"
            };
        }
    },

    methods: {
        prev() {
            if (this.direction === NEXT) {
                this.$emit("arrangeItems", NEXT);
                this.direction = PREV;
            }

            this.dontArrange = this.direction === NEXT;
            this.$refs.content.style.justifyContent = "flex-end";
            this.$refs.slider.style.transform = `translateX(${100 /
                this.itemsCount}%)`;
        },
        next() {
            this.direction = 1;
            this.$refs.content.style.justifyContent = "flex-start";
            this.$refs.slider.style.transform = `translateX(-${100 /
                this.itemsCount}%)`;
        },

        arrangeItems() {
            if (this.dontArrange) return;
            this.$emit("arrangeItems", this.direction);
            this.$refs.slider.style.transition = "none";
            this.$refs.slider.style.transform = "translateX(0)";

            requestAnimationFrame(() => {
                requestAnimationFrame(() => {
                    this.$refs.slider.style.transition =
                        "transform 0.4s ease-in";
                });
            });
        },
        updateItemsWidth(width) {
            const items = this.$refs.content.querySelectorAll(".slider > *");
            items.forEach(item => (item.style.flexBasis = width + "px"));
        }
    },

    mounted() {
        this.updateItemsWidth(this.itemWidth);
    },

    watch: {
        itemWidth(newValue) {
            this.updateItemsWidth(newValue);
        }
    }
};
</script>

<style lang="scss" scoped>
.content {
    width: 100%;
    display: flex;
    justify-content: flex-start;
    overflow: hidden;
}

.slider {
    display: flex;
    flex-shrink: 0;
    transition: transform 0.4s ease-in;

    & > * {
        flex-basis: 900px;
        flex-shrink: 0;
    }
}
</style>

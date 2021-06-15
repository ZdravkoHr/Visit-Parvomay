<template>
    <div class="wrapper" ref="wrapper">
        <div class="items-wrapper">
            <div class="content" ref="content" :style="contentStyles">
                <slot name="items"></slot>
            </div>
        </div>

        <div class="controls">
            <button @click="prev" :disabled="currentSlide === 0" class="btn">
                <i class="far fa-arrow-alt-circle-left "></i>
            </button>
            <button @click="next" :disabled="!hasNext" class="btn">
                <i class="far fa-arrow-alt-circle-right  "></i>
            </button>
        </div>
    </div>
</template>
<script>
import debounce from "lodash/debounce";
export default {
    emits: ["changeItems"],
    props: {
        itemWidth: Number,
        itemsCount: Number,
        cycle: {
            default: false
        }
    },
    data() {
        return {
            hasNext: true,
            currentSlide: 0,
            contentEl: null,
            items: null,
            contentWidth: null,
            lastMovedBy: 0
        };
    },

    methods: {
        prev: debounce(function() {
            this.currentSlide--;
            if (this.cycle) {
                this.$emit("cycle", -1);
            }
        }, 200),
        next: debounce(function() {
            this.currentSlide++;

            if (this.cycle) {
                this.$emit("changeItems", 1);
            }
        }, 200),

        initVars() {
            this.contentEl = this.$refs.content;
            this.items = this.contentEl.children;
            this.contentWidth = this.contentEl.offsetWidth;

            this.rightSpace = Number(
                window
                    .getComputedStyle(this.contentEl)
                    .gridColumnGap.slice(0, -2)
            );
        }
    },

    mounted() {
        this.initVars();
    },
    computed: {
        percentsAway() {
            return -this.percentStep * this.currentSlide;
        },
        contentStyles() {
            return {
                gridTemplateColumns: `repeat(${this.itemsCount}, ${this.itemWidth}px)`
            };
        },

        fitCount() {
            const boxesCount = Math.ceil(this.contentWidth / this.itemWidth);
            const fitCount = Math.floor(
                (this.contentWidth - (boxesCount - 1) * this.rightSpace) /
                    this.itemWidth
            );

            return fitCount;
        }
    },

    watch: {
        currentSlide(newValue, prevValue) {
            const direction = newValue > prevValue ? -1 : 1;
            const margin = +this.contentEl.style.marginLeft.slice(0, -2) || 0;
            let moveBy = this.itemWidth + this.rightSpace;
            const itemsLeft = this.items.length - newValue;

            if (itemsLeft === this.fitCount && direction === -1) {
                const lastEl = this.contentEl.children[
                    this.contentEl.children.length - 1
                ];
                const lastElRight =
                    lastEl.getBoundingClientRect().right -
                    this.contentEl.getBoundingClientRect().left;

                moveBy = lastElRight - this.contentEl.offsetWidth;
                this.lastMovedBy = moveBy;
                this.hasNext = false;
            } else {
                this.hasNext = true;
            }

            if (
                direction === 1 &&
                this.items.length - newValue === this.fitCount + 1
            ) {
                moveBy = this.lastMovedBy;
            }

            this.contentEl.style.marginLeft =
                margin + moveBy * direction + "px";
        }
    }
};
</script>

<style lang="scss" scoped>
.wrapper {
    position: relative;
}

.items-wrapper {
    overflow: hidden;
}
.content {
    display: grid;
    grid-gap: 23px;

    margin: auto;
    padding: 1rem 0;
    margin-left: 0;
    transition: margin 0.4s ease-in;
}

button {
    background: inherit;
    color: inherit;
    border: inherit;
    font-size: inherit;

    &[disabled] {
        color: gray;
    }
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 1150px) {
    .content {
        grid-gap: 15px;
    }
}
</style>

<template>
    <main-header></main-header><main-nav></main-nav>
    <info-box>
        Използвайте стрелките, за да разгледате всички паркове и площадки на
        територията на община Първомай
    </info-box>
    <section class="nature-places">
        <div class="compass"></div>
        <div class="info ta-c">
            <h2>Разходка сред природата</h2>
            <p>
                Няма нищо по-приятно от разходка на свеж въздух сред природата.
                Екипът ни Ви препоръчва да посетите тези зелени площи.
            </p>
        </div>

        <div class="carousel-wrapper">
            <component :is="carouselType" :itemWidth="itemWidth">
                <template v-slot:items>
                    <place-box
                        v-for="place in carouselItems"
                        :key="place.id"
                        :place="place"
                    >
                    </place-box
                ></template>
            </component>
        </div>
    </section>
    <info-box>
        Моля, кликнете върху някоя кутийка
    </info-box>
    <section class="remarkable-places">
        <div class="landmark"></div>
        <div class="landmark"></div>
        <h2>
            Забележителностите на общината:
        </h2>

        <div class="items" :style="rowStyles" :ref="items">
            <transition name="info">
                <place-infobox
                    class="info-box"
                    :info="activeInfo"
                    :style="infoBoxStyles"
                    v-if="infoBoxIndex > -1"
                    @goBack="goBack"
                    @goNext="goNext"
                    @close="close"
                ></place-infobox>
            </transition>
            <div
                class="col"
                @click="showInfo(j)"
                v-for="j in items"
                :key="j.id"
                :style="{ 'background-image': `url('${j.imgSrc}')` }"
                :class="isActive(j.id)"
            >
                <div class="overlay">
                    <h1 class="hover-text">
                        {{ j.name }}
                    </h1>
                </div>
            </div>
        </div>
    </section>
</template>
<script>
import Header from "@/components/header/Header";
import Navbar from "@/components/header/Navbar";
import InfoBox from "@/components/others/InfoBox";
import PlaceBox from "@/components/places/PlaceBox";
import Carousel from "@/components/others/Carousel";
import ScrollCarousel from "@/components/others/ScrollCarousel";
import PlaceInfobox from "../components/places/PlaceInfobox.vue";
export default {
    data() {
        return {
            infoBoxIndex: -1,
            activeIndex: -1,
            vw: document.documentElement.offsetWidth,
            carouselItems: [
                {
                    id: 0,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                },
                {
                    id: 1,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                },
                {
                    id: 2,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                },
                {
                    id: 3,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                },
                {
                    id: 4,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                },
                {
                    id: 5,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                },
                {
                    id: 6,
                    imgSrc:
                        "https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png",
                    title: "Lorem Ipsum",
                    info: "Lorem ispum is simply dummy"
                }
            ],

            items: [
                {
                    id: 0,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 1,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Ресторант "Хипноза"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 2,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 3,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 4,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 5,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 6,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 7,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                },
                {
                    id: 8,
                    imgSrc: "https://mapio.net/images-p/49527160.jpg",
                    name: 'Читалище "Св. Св. Кирил и Методий"',
                    info: `Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Pellentesque auctor lorem at tellus ornare condimentum. Quisque
                    lobortis velit nisi, quis hendrerit arcu auctor ut. Nulla
                    facilisi. Donec et rutrum lacus. Aliquam lectus massa, ultricies
                    eu orci ac, condimentum scelerisque dolor. Aenean eleifend
                    facilisis velit. Etiam sodales orci quis gravida consectetur.
                    Etiam pellentesque nibh aliquam, egestas metus et, maximus orci.
                    Donec vel blandit elit. Ut in odio vel ligula dictum lobortis.
                    Duis tincidunt est ex. Morbi nec erat ut lorem varius accumsan.
                    Mauris suscipit fermentum est sed viverra. Sed sollicitudin,
                    purus at imperdiet laoreet, quam elit fringilla mi, nec blandit
                    enim velit in enim. Pellentesque id odio vitae mauris varius
                    iaculis vel non dolor. Aenean pretium varius risus a convallis.`
                }
            ]
        };
    },
    methods: {
        showInfo(item) {
            if (this.activeIndex === item.id) return;
            const rowIndex = Math.trunc(item.id / this.itemsPerRow) + 1;
            this.activeIndex = item.id;
            this.infoBoxIndex = -1;
            setTimeout(() => {
                this.infoBoxIndex = rowIndex;
                console.log("info box index: ", this.infoBoxIndex);
            });
        },
        goBack() {
            this.activeIndex =
                (this.items.length + this.activeIndex - 1) % this.items.length;
        },
        goNext() {
            this.activeIndex = (this.activeIndex + 1) % this.items.length;
        },
        close() {
            this.infoBoxIndex = -1;
            this.activeIndex = -1;
        }
    },

    computed: {
        itemsPerRow() {
            if (this.vw > 750) {
                return 3;
            }

            if (this.vw > 400) {
                return 2;
            }

            return 1;
        },
        rowsCount() {
            return Math.ceil(this.items.length / this.itemsPerRow);
        },
        rowStyles() {
            const styles = {
                "grid-template-columns": `repeat(${this.itemsPerRow}, 1fr)`
            };

            const rowHeight = this.vw > 400 ? "min(23vw, 300px)" : "300px";

            if (this.infoBoxIndex === -1) {
                styles[
                    "grid-template-rows"
                ] = `repeat(${this.rowsCount}, ${rowHeight})`;
            } else if (this.infoBoxIndex === this.rowsCount) {
                styles[
                    "grid-template-rows"
                ] = `repeat(${this.rowsCount}, ${rowHeight}) auto`;
            } else {
                styles["grid-template-rows"] = `repeat(${
                    this.infoBoxIndex
                }, ${rowHeight}) auto repeat(${this.rowsCount -
                    this.infoBoxIndex}, ${rowHeight})`;
            }

            return styles;
        },
        infoBoxStyles() {
            if (this.infoBoxIndex < 0) {
                return {};
            }
            return {
                "grid-row-start": this.infoBoxIndex + 1,
                "grid-column-end": this.itemsPerRow + 1
            };
        },
        activeInfo() {
            return this.items[this.activeIndex];
        },
        isActive() {
            const activeIndex = this.activeIndex;
            return id => ({ active: id === activeIndex });
        },

        carouselType() {
            return this.vw > 650 ? "carousel" : "scrollCarousel";
        },
        itemWidth() {
            if (this.vw > 1150) {
                return 240;
            }

            return 160;
        }
    },

    mounted() {
        window.addEventListener("resize", () => {
            this.vw = document.documentElement.offsetWidth;
        });
    },

    components: {
        MainHeader: Header,
        MainNav: Navbar,
        InfoBox,
        PlaceBox,
        Carousel,
        ScrollCarousel,
        PlaceInfobox
    }
};
</script>

<style lang="scss" scoped>
@use '../styles/partials/mixins' as *;

.nature-places {
    background-color: var(--clr-dark-1);
    color: #fff;
    display: flex;
    padding: 1.5rem 3rem;
    position: relative;
    overflow: hidden;

    .compass {
        position: absolute;
        top: -6%;
        left: 9%;
        width: 36%;
        opacity: 0.1;
        z-index: 0;
        height: 100%;
        background: url(../assets/vectors/compass.svg) no-repeat center center;
        background-size: cover;
    }

    .info {
        flex: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        max-width: 30%;
        z-index: 1;
    }

    .carousel-wrapper {
        flex: 1.5;
        padding-left: 20px;
        max-width: 70%;

        ::v-deep(.controls) {
            color: var(--clr-other-green);
            text-align: right;
            font-size: 1.8rem;

            & > * {
                margin-right: 5px;
                cursor: pointer;
                padding: 0.1rem;
            }

            padding-right: 20px;
        }
    }
}

.remarkable-places {
    padding: 3% 0;
    position: relative;
    overflow: hidden;
    h2 {
        width: 60%;
    }
    .landmark {
        position: absolute;
        height: 50%;
        &:first-child {
            background: url("../assets/vectors/landmark1.svg") no-repeat center
                center;
            left: -13%;
            top: -8%;
            width: 30%;
            opacity: 0.1;
        }
        &:nth-child(2) {
            background: url("../assets/vectors/landmark2.svg") no-repeat center
                center;
            right: -8%;
            bottom: -10%;
            width: 29%;
            height: 44%;
            opacity: 0.1;
        }
    }
}

h2 {
    text-align: center;
    color: var(--clr-other-green);
    font-size: 2.6rem;
    letter-spacing: 4px;
    margin: 0 auto 3%;
}

p {
    font-size: 1.3rem;
    color: #dadada;
    letter-spacing: 1px;
}

.items {
    display: grid;
    grid-gap: 1rem;
    margin-bottom: 10px;
    padding: 0 3rem;
}

.col {
    background-size: cover;
    background-position: center;
    cursor: pointer;
    user-select: none;
    position: relative;

    &:hover,
    &.active {
        .overlay {
            opacity: 1;
        }
    }
}

.items .info-box {
    position: relative;
    display: grid;
    grid-template-columns: 1fr 2fr;
    grid-column-start: 1;
}

.overlay {
    @include overlay(0.7, #009966);
    color: white;
    font-size: 2vw;
    font-weight: 900;
    letter-spacing: 5px;
    text-align: center;
    opacity: 0;
    transition: 0.5s ease-out;
    padding: 0 1rem;
    display: flex;
    align-items: center;
    justify-content: center;
}
.hover-text {
    font-size: 2.8vw;
}

.info-enter-from {
    transform: translateY(-100%);
    opacity: 0;
}

.info-enter-active {
    transition: opacity 2s, transform 0.5s;
}

.info-enter-to {
    transform: translateY(0);
    opacity: 1;
}

.info-leave-active {
    transition: 0.5s;
}

.info-leave-to {
    opacity: 0;
    transform: translateY(-100%);
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 1150px) {
    .nature-places {
        padding: 1.5rem 2rem;
        .info {
            max-width: 40%;
        }
        .carousel-wrapper {
            max-width: 60%;
        }
        .compass {
            width: 55%;
            height: 110%;
            top: -18%;
        }
    }
    h2 {
        font-size: 2.2rem;
    }
    p {
        font-size: 1.1rem;
    }
}

@media (max-width: 850px) {
    h2 {
        font-size: 2rem;
    }
    p {
        font-size: 1rem;
    }
}

@media (max-width: 750px) {
    h2 {
        font-size: 1.7rem;
    }
    p {
        font-size: 0.95rem;
    }
    .nature-places .carousel-wrapper {
        max-width: 57%;
    }
    .nature-places .info {
        max-width: 43%;
    }
}

@media (max-width: 650px) {
    h2 {
        font-size: 1.7rem;
    }
    .nature-places h2 {
        font-size: 2rem;
    }
    p {
        font-size: 1rem;
    }
    .nature-places {
        padding-left: 0;
        padding-right: 0;
        flex-direction: column;
    }
    .nature-places .carousel-wrapper {
        max-width: 100%;
    }
    .nature-places .info {
        max-width: 75%;
        margin: 2% auto;
    }
    .nature-places .compass {
        height: 58%;
        top: -15%;
        right: 5%;
        left: unset;
    }
}

@media (max-width: 500px) {
    .remarkable-places h2 {margin: auto; width: 90%; font-size: 5vw; margin-bottom: 3%;}
    .nature-places .info, .nature-places .info h2{margin-bottom: 5%;}
    .nature-places .compass{width: 80%; height: 80%;}
}

@media (max-width: 400px) {
    .items {
        padding: 0;
    }
    .hover-text {
        font-size: min(14vw, 30px);
    }
}
</style>

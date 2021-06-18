<template>
    <main-header></main-header><main-nav></main-nav>
    <info-box
        >Вижте най-популярните заведения сред посетителите на сайта</info-box
    >
    <section class="first-section">
        <div class="burger"></div>
        <div class="box-holder">
            <div class="with-text">
                <restaurantsReview>
                    <template v-slot:icons>
                        <i class="fas fa-long-arrow-alt-up icon-size green"></i>
                        <i class="fas fa-star icon-size green"></i>
                        <h3>50</h3>
                        <i class="fas fa-utensils icon-size red"></i>
                    </template>
                </restaurantsReview>
            </div>
            <div class="with-text">
                <bigReview class="">
                    <template v-slot:icons>
                        <i class="fas fa-long-arrow-alt-up icon-size green"></i>
                        <i class="fas fa-star icon-size green"></i>
                        <h3>50</h3>
                        <i class="fas fa-utensils icon-size red"></i>
                    </template>
                </bigReview>
            </div>
            <div class="with-text">
                <restaurantsReview>
                    <template v-slot:icons>
                        <i class="fas fa-long-arrow-alt-up icon-size green"></i>
                        <i class="fas fa-star icon-size green"></i>
                        <h3>50</h3>
                        <i class="fas fa-utensils icon-size red"></i>
                    </template>
                </restaurantsReview>
            </div>
        </div>
    </section>
    <section class="all-restaurants">
        <div class="title">
            <h1>Всички ресторанти и заведения:</h1>
        </div>
        <InfoBox>Моля, кликнете върху някоя кутийка</InfoBox>
        <div class="restaurants-holder">
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
            <restaurantsReview class="">
                <template v-slot:icons>
                    <i class="fas fa-star icon-size green"></i>
                    <h3>50</h3>
                    <i class="fas fa-utensils icon-size red"></i>
                </template>
            </restaurantsReview>
        </div>
    </section>
    <section class="comment">
        <div class="carousel-wrapper">
            <slider
                :itemWidth="testimonialWidth"
                :itemsCount="itemsCount"
                @arrangeItems="arrangeItems"
            >
                <template v-slot:items>
                    <testimonial
                        v-for="t in testimonials"
                        :key="t.id"
                        :info="t"
                    ></testimonial>
                </template>
            </slider>
        </div>
    </section>
</template>
<script>
import Header from "@/components/header/Header";
import Navbar from "@/components/header/Navbar";
import RestaurantsReview from "@/components/restaurants/RestaurantsReview";
import BigReview from "@/components/restaurants/BigReview";
import InfoBox from "@/components/others/InfoBox";
import Slider from "@/components/others/Slider";
import Testimonial from "@/components/restaurants/Testimonial";

export default {
    data() {
        return {
            testimonialWidth: 0,

            testimonials: [
                {
                    id: 0,
                    user: {
                        img: {
                            path: "parvomay/User-Icon.png",
                            size: 120
                        },
                        name: "Username"
                    },

                    comment: {
                        place: "Ресторант Стремон",
                        content:
                            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec sit amet congue ante, a pretium ligula. Donec sit amet libero vel sapien tempus eleifend ac mattis risus. Nam ut laoreet tellus. Donec eget ornare arcu. Praesent scelerisque, tortor ut dignissim egestas, turpis augue cursus leo, eget ultrices dolor est id augue. Nam at placerat mauris. Aenean velit purus, posuere in congue nec, tempus accumsan urna. Aenean efficitur sit amet quam pretium vulputate. Duis porta rutrum viverra. Donec pretium vestibulum arcu vel vulputate. Suspendisse potenti. "
                    }
                },
                {
                    id: 1,
                    user: {
                        img: {
                            path: "parvomay/User-Icon.png",
                            size: 120
                        },
                        name: "Username 2"
                    },

                    comment: {
                        place: "Ресторант Стремон 2",
                        content:
                            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec sit amet congue ante, a pretium ligula. Donec sit amet libero vel sapien tempus eleifend ac mattis risus. Nam ut laoreet tellus. Donec eget ornare arcu. Praesent scelerisque, tortor ut dignissim egestas, turpis augue cursus leo, eget ultrices dolor est id augue. Nam at placerat mauris. Aenean velit purus, posuere in congue nec, tempus accumsan urna. Aenean efficitur sit amet quam pretium vulputate. Duis porta rutrum viverra. Donec pretium vestibulum arcu vel vulputate. Suspendisse potenti. "
                    }
                },
                {
                    id: 2,
                    user: {
                        img: {
                            path: "parvomay/User-Icon.png",
                            size: 120
                        },
                        name: "Username 3"
                    },

                    comment: {
                        place: "Ресторант Стремон 3",
                        content:
                            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec sit amet congue ante, a pretium ligula. Donec sit amet libero vel sapien tempus eleifend ac mattis risus. Nam ut laoreet tellus. Donec eget ornare arcu. Praesent scelerisque, tortor ut dignissim egestas, turpis augue cursus leo, eget ultrices dolor est id augue. Nam at placerat mauris. Aenean velit purus, posuere in congue nec, tempus accumsan urna. Aenean efficitur sit amet quam pretium vulputate. Duis porta rutrum viverra. Donec pretium vestibulum arcu vel vulputate. Suspendisse potenti. "
                    }
                }
            ]
        };
    },

    mounted() {
        this.testimonialWidth = 900;
    },

    computed: {
        itemsCount() {
            return this.testimonials.length;
        }
    },

    methods: {
        arrangeItems(direction) {
            if (direction === 1) {
                this.testimonials.push(this.testimonials.shift());
                return;
            }

            this.testimonials.unshift(this.testimonials.pop());
        }
    },

    components: {
        MainHeader: Header,
        MainNav: Navbar,
        RestaurantsReview,
        InfoBox,
        BigReview,
        Testimonial,
        Slider
    }
};
</script>
<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;
.first-section {
    background-color: #f6f6f6;
    padding: 5% 0;
    height: 90vh;
    position: relative;
    overflow: hidden;
}

.burger {
    position: absolute;
    right: -17%;
    top: -27%;
    width: 51%;
    height: 100%;
    background: url(../assets/vectors/burger.svg) no-repeat center center;
    background-size: cover;
    opacity: 0.1;
}

.box-holder {
    display: flex;
    width: 60%;
    height: 100%;
    margin: 0 auto;
    .box {
        height: 100%;
        align-self: flex-end;
    }
}

.all-restaurants {
    background: var(--clr-dark-2);
    margin: 0;
    width: 100%;

    .title {
        color: #f3f3f3;
        font-size: 22px;
        text-align: center;
        padding: 2% 0;
        letter-spacing: 4px;
        h1 {
            font-weight: 100;
        }
    }
}

.restaurants-holder {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 5% 4%;
    padding: 5% 10% 12%;
    .box {
        height: 22rem;
        color: #dadada;
        border: none;
    }
    .img {
        border: 1px solid #626262;
    }
}

.with-text {
    align-items: flex-end;
    display: flex;
    flex-direction: row;
    width: 40%;
    margin: 0 2%;
    &:first-child {
        height: 90%;
        width: 30%;
        align-self: flex-end;
        justify-self: flex-end;
    }
    &:last-child {
        height: 80%;
        width: 30%;
        align-self: flex-end;
        justify-self: flex-end;
    }
}

.comment {
    background-image: linear-gradient(
            to bottom,
            rgb(0 153 102 / 67%),
            rgb(0 153 102 / 50%)
        ),
        url("~@/assets/parvomay/whitefood.jpg");

    height: 90vh;
    background-size: cover;
    display: flex;
    align-items: center;
    justify-content: center;

    .carousel-wrapper {
        max-width: 990px;
        position: relative;

        ::v-deep(.content) {
            border-radius: 10px;
        }

        ::v-deep(.controls) {
            display: flex;
            justify-content: space-between;
            z-index: 4;
            width: calc(100% + 135px);
            margin-left: -45px;
            top: 50%;
            position: absolute;
            transform: translateY(calc(-50% + 45px));

            & > * {
                background: transparent;
                color: #fff;
                font-size: 40px;
            }
        }
    }
}

.icon-size {
    font-size: 22px;
}

.green {
    color: var(--clr-other-green);
}

.icon-holder {
    display: flex;
    align-items: center;

    h3 {
        font-size: 16px;
        color: #d30031;
    }

    .red {
        color: #d30031;
    }
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 1150px) {
    .first-section {
        height: 80vh;
    }
    .with-text {
        width: 30%;
        &:first-child,
        &:last-child {
            width: 25%;
        }
    }
    .box-holder {
        width: 80%;
    }
    .restaurants-holder {
        padding: 5% 3% 12%;
        grid-gap: 4% 3%;
        .box {
            height: 20rem;
        }
    }
}

@media (max-width: 850px) {
    .first-section {
        height: 60vh;
    }
    .with-text {
        width: 35%;
        &:first-child,
        &:last-child {
            width: 30%;
        }
    }
    .info-box {
        padding: 20px 30px;
    }
    .all-restaurants .title {
        font-size: 1.2rem;
    }
    .restaurants-holder {
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 2.5% 5%;
        padding-bottom: 18%;
    }

    .restaurants-holder .box {
        height: 17rem;
    }
}

@media (max-width: 750px) {
    .box-holder {
        width: 100%;
    }
    .with-text {
        width: 33%;
        &:first-child,
        &:last-child {
            width: 27%;
        }
    }
    .icon-size {
        font-size: 1rem;
    }
    .rating p {
        font-size: 0.8rem;
    }
}

@media (max-width: 650px) {
    .with-text:first-child,
    .with-text:last-child {
        display: none;
    }
    .box-holder {
        justify-content: center;
    }
    .first-section {
        height: 70vh;
    }
    .restaurants-holder {
        grid-template-columns: repeat(2, 1fr);
        height: 125rem;
        padding: 8% 10%;
    }
}

@include mobile() {
    .first-section {
        padding: 8% 0;
        height: 80vh;
    }
    .with-text {
        width: 50%;
    }
    .restaurants-holder {
        grid-template-columns: 1fr;
        grid-row-gap: 0;
        height: 300rem;
    }
    .restaurants-holder .box {
        height: 23rem;
        width: 70%;
    }
    .all-restaurants .title {
        font-size: 5vw;
        width: 90%;
        margin: auto;
        padding: 3% 0;
        letter-spacing: 2px;
    }
}
</style>

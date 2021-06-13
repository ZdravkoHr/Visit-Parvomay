<template>
    <header class="main-header">
        <div class="burger-icon" :class="burgerStyle" @click="toggleMobileNav">
            <div class="line"></div>
            <div class="line"></div>
            <div class="line"></div>
        </div>
        <div class="grey-box"></div>
        <div class="header-img">
            <div class="overlay"></div>
            <div class="flex-cy header-text">
                <h1>Община <br />Първомай</h1>
                <p class="flex-ex">
                    Lorem Ipsum is<br />
                    simply dummy<br />
                    text of the<br />
                    printing and<br />
                    typesetting industry.<br />
                    Lorem Ipsum
                </p>
            </div>
        </div>
    </header>

    <teleport to="#body">
        <div class="mobile-nav" v-if="openedMobileNav">
            <div class="menu">
                <router-link to="home">Начало</router-link>

                <router-link to="places">Места</router-link>

                <router-link to="restaurants">Ресторанти</router-link>

                <router-link to="tourism">Туризъм</router-link>

                <router-link to="celebrations">Празненства</router-link>

                <router-link to="map">Карта</router-link>
            </div>
        </div>
    </teleport>
</template>

<script>
export default {
    data() {
        return { openedMobileNav: false };
    },
    methods: {
        toggleMobileNav() {
            this.openedMobileNav = !this.openedMobileNav;
        }
    },
    computed: {
        burgerStyle() {
            return {
                "close-icon": this.openedMobileNav
            };
        }
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;

.main-header {
    height: 400px;
    min-height: 80vh;
    width: 100%;
    display: flex;

    .burger-icon {
        position: absolute;
        z-index: 900;
        top: 10px;
        left: 10px;
        cursor: pointer;
        display: none;

        .line {
            width: 35px;
            margin-top: 5px;
            background: #f6f6f6;
            height: 6px;
            border-radius: 4px;
            transition: 0.4s ease-in;
        }

        &.close-icon {
            position: fixed;
            .line:nth-child(1) {
                transform: rotate(45deg);
                position: relative;
                top: 10px;
            }

            .line:nth-child(3) {
                transform: rotate(-45deg);
            }
            .line:nth-child(2) {
                display: none;
            }
        }
    }

    .grey-box {
        width: 20%;
        background: var(--clr-dark-3);
    }

    h1 {
        color: var(--clr-light-gray2);
        font-size: var(--txt-lg);
        line-height: var(--txt-lg);
        left: -4rem;
        position: relative;
        letter-spacing: 4px;
    }

    .header-img {
        background-image: url("~@/assets/parvomay/parvomay.jpg");
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        position: relative;
        height: 100%;
        width: 80%;
        display: flex;
        flex-direction: column;

        .overlay {
            @include overlay(
                1,
                linear-gradient(
                    to bottom,
                    rgba(#1c1e1b, 0.4),
                    rgba(#238a65, 0.5)
                )
            );
            z-index: 1;
        }

        * {
            z-index: 2;
        }
    }

    .header-text {
        flex: 1;
    }
    h2 {
        text-align: right;
        color: var(--clr-light-gray2);
        margin: 10px 20px 0px 0px;
    }

    p {
        letter-spacing: 2.5px;
        font-size: calc(var(--txt-lg) / 3);
        color: var(--clr-light-gray2);
        padding-right: 100px;
        text-align: center;
        flex: 1;
    }
}

.mobile-nav {
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 600;
    @include overlay(0.9, #009966);
    position: fixed;
    display: flex;
    align-items: center;
    justify-content: center;

    .menu {
        width: 100%;
        & > * {
            display: block;
            color: #f6f6f6;
            text-align: center;
            text-decoration: none;
            padding: 0.75rem 1.25rem;
            font-family: "Book Antiqua", serif;
            font-size: 11vw;
            letter-spacing: 4px;
            border-bottom: 1px solid #f3f3f378;
        }
    }
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 850px) {
    .main-header {
        min-height: 70vh;
    }
}

@media (max-width: 750px) {
    .main-header {
        min-height: 20vh;
        max-height: 50vh;

        .header-img {
            width: 100%;
        }

        .header-text {
            justify-content: center;

            h1 {
                text-align: center;
                left: 0;
                line-height: 1.3;
                font-size: min(10vw, 50px);
            }
        }

        .grey-box {
            display: none;
        }

        p {
            display: none;
        }
    }
}

@include mobile() {
    .main-header .burger-icon {
        display: block;
    }
}
</style>

<template>
    <main-header></main-header>
    <main-nav></main-nav>
    <info-box :showIcon="false">
        Добре дошли в нашия уебсайт! Тук ще откриете интересни забележителности,
        цветни кътчета, гостоприемни заведения и интересна информация за общи
    </info-box>

    <section class="what-can-you-find ">
        <div class="lens"></div>
        <div class="wcyf-container">
            <div class="info">
                <h2>
                    Какво мога да намеря в община Първомай?
                </h2>

                <p>
                    Подбрали сме Ви едни от най-интересните забележителности,
                    които може да намерите на територията на община Първомай.
                </p>

                <router-link class="btn-primary" to="places"
                    >Към места &gt; &gt;</router-link
                >
            </div>

            <div class="images">
                <div class="col">
                    <div class="img-holder">
                        <div class="overlay"></div>
                        <div class="img">
                            <span class="title">Читалище</span>
                        </div>
                    </div>
                </div>
                <div class="col">
                    <div class="img-holder">
                        <div class="overlay"></div>
                        <div class="img">
                            <span class="title">Читалище</span>
                        </div>
                    </div>
                    <div class="img-holder">
                        <div class="overlay"></div>
                        <div class="img">
                            <span class="title">Читалище</span>
                        </div>
                    </div>
                </div>
                <div class="col">
                    <div class="img-holder">
                        <div class="overlay"></div>
                        <div class="img">
                            <span class="title">Читалище</span>
                        </div>
                    </div>
                    <div class="img-holder">
                        <div class="overlay"></div>
                        <div class="img">
                            <span class="title">Читалище</span>
                        </div>
                    </div>
                </div>
                <div class="col">
                    <div class="img-holder">
                        <div class="overlay"></div>
                        <div class="img">
                            <span class="title">Читалище</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <info-box :showIcon="false" class="info-shadow">
        Не стойте гладни, а опитайте специалитетите на нашите ресторанти! Също
        така не пропускайте чаша топло кафе в уютните ни заведени!
    </info-box>

    <section class="restaurant-boxes ">
        <div class="boxes-holder">
            <restaurant-box class="left hipnoza"></restaurant-box>
            <restaurant-box class="hipnoza"></restaurant-box>
            <restaurant-box class="hipnoza"></restaurant-box>
            <restaurant-box class="hipnoza"></restaurant-box>
        </div>

        <div class="button-wrapper">
            <router-link class="button-restaurant btn-primary" to="restaurants">
                Към ресторанта &gt; &gt;
            </router-link>
        </div>
    </section>
</template>
<script>
import Header from "@/components/header/Header";
import Navbar from "@/components/header/Navbar";
import RestaurantBox from "@/components/home/RestaurantBox";
import InfoBox from "@/components/others/InfoBox";
export default {
    components: { RestaurantBox, InfoBox, MainHeader: Header, MainNav: Navbar }
};
</script>
<style lang="scss" scoped>
@use '../styles/partials/mixins' as *;

.img {
    width: 100%;
    height: 100%;
    background: url("https://chitalishteparvomay1894.com/wp-content/uploads/2019/01/cropped-zaglavna.png")
        no-repeat center center;
    background-size: cover;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
}
.restaurant-boxes {
    background-color: var(--clr-dark-1);
    padding: 2rem;
}
.button-restaurant {
    padding: 8px;
    border: 1px solid #dadada4d;
    border-radius: 5px;
    text-decoration: none;
}

.button-wrapper {
    justify-content: flex-end;
    display: flex;
    max-width: 80%;
    margin: auto;
}

.boxes-holder {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    max-width: 80%;
    margin: auto;
    grid-column-gap: 5%;
    padding: 3rem 0;
    height: 25rem;

    .box {
        background-size: cover;
        border: 1px solid #626262;
        position: relative;
        box-shadow: 0 0 59px rgb(28 30 27 / 38%);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }

    .hipnoza {
        background-image: url("../assets/parvomay/hiphop.jpeg");
    }
}
.wrapper-section {
    background-color: var(--clr-light-gray1);
}

.what-can-you-find {
    background: var(--clr-light-gray1);
    position: relative;

    .lens {
        position: absolute;
        bottom: -1%;
        left: -10%;
        z-index: 0;
        width: 63%;
        height: 100%;
        background: url("../assets/vectors/lens.svg") no-repeat center center;
        background-size: cover;
        opacity: 0.1;
    }
}

.wcyf-container {
    display: flex;
    padding: 2rem 0;
    margin: auto;
    max-width: 1100px;

    .info {
        width: 30%;
        z-index: 1;
    }

    h2 {
        color: #058a5e;
        letter-spacing: 2px;
        margin-top: 5rem;
        font-size: 1.8rem;
    }

    p {
        font-size: 1rem;
        margin: 30px 0 20px 0;
        line-height: 1.6;
        color: #2b2d28;
        letter-spacing: 1px;
    }

    .images {
        display: grid;
        width: 70%;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-gap: 3%;

        .col {
            &:nth-child(1) {
                margin-top: 15rem;
            }
            &:nth-child(2),
            &:nth-child(4) {
                margin-top: 6.5rem;
            }
        }

        .img-holder {
            height: min(242px, 20vw);
            margin-bottom: 40px;
            position: relative;
            user-select: none;
        }

        .title {
            color: #fff;
            font-size: 1.3rem;
            text-align: center;
            margin-bottom: 4%;
            z-index: 1;
            font-family: Book Antique, serif;
            letter-spacing: 2px;
        }

        .overlay {
            @include overlay(
                1,
                linear-gradient(to bottom, rgba(0, 0, 0, 0), 75%, #015136)
            );
        }
    }
}

.info-shadow {
    box-shadow: 0 5px rgba(#1c1e1b, 0.21);
}

.info-box {
    font-family: "Book Antiqua", serif;
}
.info-box p {
    width: 80%;
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 1150px) {
    .wcyf-container {
        max-width: 900px;
        padding: 2rem;

        .info {
            width: 35%;
        }
        .images {
            width: 65%;
        }
    }
    .boxes-holder {
        max-width: 85%;
    }
    .button-wrapper {
        max-width: 85%;
    }
}

@media (max-width: 850px) {
    .wcyf-container .images .title {
        font-size: 1rem;
    }
    .boxes-holder {
        max-width: 100%;
        height: 20rem;
    }
    .button-wrapper {
        max-width: 100%;
    }
}

@media (max-width: 750px) {
    .wcyf-container {
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 4rem 2rem;
    }
    .wcyf-container .images {
        display: none;
    }
    .wcyf-container .info {
        width: 100%;
    }
    .wcyf-container .info h2 {
        margin-top: 0;
    }
    .boxes-holder {
        grid-template-columns: repeat(2, 1fr);
        grid-gap: 1% 9%;
        width: 70%;
        padding: 1rem 0;
        height: 35rem;
    }
    .boxes-holder .box {
        height: 15rem;
    }
    .button-wrapper {
        max-width: 70%;
    }
}

@include mobile() {
    .restaurant-boxes {
        padding: 2rem 0;
    }
}

@media (max-width: 450px) {
    .boxes-holder {
        width: 80%;
    }
    .button-wrapper {
        max-width: 80%;
    }
    .what-can-you-find .lens {
        left: -30%;
        width: 110%;
    }
}

@media (max-width: 350px) {
    .boxes-holder {
        grid-template-columns: 1fr;
        width: 60%;
        grid-row-gap: 3%;
        height: 73rem;
    }
    .box {
        height: 20rem;
    }
    .button-wrapper {
        max-width: 80%;
    }
}
</style>

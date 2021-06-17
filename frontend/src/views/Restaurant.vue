d<template>
    <main-nav></main-nav>
    <header class="main-header">
        <div class="header-img">
            <div class="overlay"></div>
        </div>
        <div class="holder">
            <div class="circle"></div>
            <div class="rating-holder">
                <div class="rating">
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                    <i class="fas fa-star"></i>
                </div>
                <div class="btn-primary">
                    Посетих <i class="fas fa-utensils"></i>
                </div>
            </div>
        </div>
    </header>
    <section>
        <h1>Ресторант <span>Хипноза</span></h1>
        <h3>Къде се намира?</h3>
        <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. </p>
        <h3>Работно време:</h3>
        <p>от 10 до 18ч.</p>
        <h3>Какво се предлага:</h3>
        <img src="~@/assets/parvomay/menu.jpg"/>
        <h3>Какво казват клиентите:</h3>
        <div class="review">
            <div class="user"></div>
            <h4>username</h4>
            <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
        </div>
    </section>
</template>
<script>
import Navbar from "@/components/header/Navbar";


export default {
    components: {
        mainNav: Navbar
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
    position: relative;

    .header-img {
        background-image: url("~@/assets/parvomay/parvomay.jpg");
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        position: relative;
        height: 100%;
        width: 100%;
        display: flex;
        flex-direction: column;

        .overlay {
            @include overlay(
                1,
                linear-gradient(
                    to bottom,
                    rgb(28 30 27 / 40%),
                    rgb(28 30 27 / 40%)
                )
            );
            z-index: 1;
        }

        * {
            z-index: 2;
        }
    }
}

.holder {
    display: flex; 
    flex-direction: row;
    height: 23vw;
    padding: 0 3%;
    position: absolute;
    width: 100%;
    z-index: 2;
    bottom: -30%;
    .circle {
        width: 25%;
        height: 100%;
        background: blue;
        border: 10px solid #e8e8e8;
        border-radius: 50%;
        filter: drop-shadow(0 0 20px #00000066);
    }
    .rating-holder {
        height: 45%;
        width: 75%;
        display: flex;
        flex-direction: row;
        align-items: flex-end;
        justify-content: space-between;
        font-size: 1.4rem;
        .rating {
            font-size: 2.4rem; 
            margin-left: 1rem; 
            color: #009966;
            i {margin-right: 2px; filter: drop-shadow(0 0 20px #000000cf);}
        }
        .btn-primary {
            padding: 0.8rem 1.3rem; 
            font-weight: 100; 
            color: #f6f6f6;
            box-shadow: 0 0 20px #2122228a;
        }
    }
}

section {
    padding: 3rem 4rem;
    h1 {
        font-size: 3.5rem;
        color: #1c1e1b;
        margin: 0 0 6% 30%;
        span {color: #009966;}
    }
    h3 {
        font-size: 2.3rem;
        color: #009966;
        margin: 1.5rem 0 0.3rem;
    }
    img {max-width: 30rem; margin: 1rem 5rem;}

    .review {
        width: 80%;
        margin: 1rem auto;
        h4 {color: #009966; margin-bottom: 1rem;}
        .user {
            background: url("~@/assets/parvomay/User-Icon.png") center center; 
            background-size: cover;
            border-radius: 50%;
            width: 5rem; 
            height: 5rem;
        }
    }
}
</style>

<template>
    <a class="box" href="#">
        <div class="img">
        <div class="star">
            4
        </div>
        <div class="dark-overlay"></div>
        </div>
        <div class="rating">
            <p>Ресторант<br> "Хипоноза"</p>
            <div class="icon-holder">
             <slot name="icons">   

            </slot>
        </div>
        </div>

    </a>
</template>

<style lang="scss" scoped>
@use '../../styles/partials/mixins' as *;
.star {
    width: 4rem;
    height: 4rem;
    background-color: var(--clr-other-green);
    clip-path: polygon(
        50% 0%,
        61% 35%,
        98% 35%,
        68% 57%,
        79% 91%,
        50% 70%,
        21% 91%,
        32% 57%,
        2% 35%,
        39% 35%
    );
    display: flex;
    align-items: center;
    justify-content: center;
    color: #f3f3f3;
    transform: translate(-50%, -50%) rotate(-16deg);
    position: relative;
    z-index: 1;
}

.img{
    position:relative;
    background-image: url("../../assets/parvomay/hiphop.jpeg");
    height: 100%;
    background-size: cover;
    border: 1px solid #626262;
}
.dark-overlay {
    @include overlay(0.3);
    transition: ease-in-out 0.5s;
}
.box {
    background-size: cover;
    width: 100%;
    margin: 0 auto;
    text-decoration: none;
    color: #2b2d28;
	display: flex;
	flex-direction: column;
    &:hover {
        .dark-overlay {
            @include overlay(0);
        }
        p {
            text-decoration-color: #dadada54;
        }
    }
}

.rating{
    display: flex;
    justify-content: space-between;
    align-items: center;
    p{
        margin-top: 2%;
        font-size: 1.4rem;
        transition: ease-in-out 0.5s;
        text-decoration: underline;
        text-decoration-color: #dadada00;
    }
}

.green{
    color: var(--clr-other-green);  
}

.icon-holder{
    display: flex;

                h3{
                    font-size: 16px;
                    color: #d30031;
                }

                .red{
                    color: #d30031;
                }

}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media(max-width: 1150px) {
    .star {width:3.5rem; height:3.5rem;}
    .rating p {font-size: 1rem;}
}
</style>

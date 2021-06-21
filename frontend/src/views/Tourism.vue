<template
    ><main-header></main-header><main-nav></main-nav>
    <section class="flex tourism-container tourism-info">
        <div class="img-container">
            <div class="img"></div>
        </div>
        <div class="ta-c p-x-2 text">
            <h2>Община Първомай</h2>
            <p>
                Lorem ipsum dolor sit amet consectetur, adipisicing elit.
                Aspernatur perspiciatis autem, cupiditate explicabo placeat quas
                repudiandae, ut, consequatur dolorum dolor provident maiores
                debitis temporibus velit? Aut excepturi in error adipisci sed,
                ratione, obcaecati accusantium cumque eveniet minima repudiandae
                odit dolorem, optio sit sunt accusamus officiis pariatur vel
                magnam doloribus eos.
            </p>
        </div>
    </section>
    <section class="dropdowns">
        <dropdown> </dropdown> <dropdown> </dropdown> <dropdown> </dropdown>
    </section>
</template>
<script>
import Header from "@/components/header/Header";
import Navbar from "@/components/header/Navbar";
import Dropdown from "@/components/tourism/Dropdown.vue";
export default {
    components: {
        MainHeader: Header,
        MainNav: Navbar,
        Dropdown
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;
.tourism-container {
    padding: 3rem 0;
    margin-left: auto;
    margin-right: auto;
    max-width: 1300px;
    height: 70vh;
    & > * {
        flex: 1;
    }
    h2 {
        font-size: 2.8rem;
        color: var(--clr-other-green);
        margin-bottom: 20px;
    }
    p {
        letter-spacing: 1px;
        font-size: 1.2rem;
    }
    .text {
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
    .img-container {
        transform: scale(0.8);
        position: relative;
        &::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: var(--clr-other-green);
            z-index: 4;
            top: -40px;
            left: -40px;
        }
        .img {
            z-index: 5;
            position: relative;
            background: url("../assets/parvomay/obshtina.jpg") no-repeat center
                center;
            background-size: cover;
            height: 100%;
            width: 100%;
        }
    }
}
* {
    letter-spacing: 2px;
}
.dropdowns {
    margin-left: auto;
    margin-right: auto;
    max-width: 1300px;
    margin-bottom: 2rem;
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 1150px) {
    .tourism-container h2 {
        font-size: 2.3rem;
    }
    .tourism-container p {
        font-size: 1rem;
    }
    header h2 {
        font-size: 2.2rem;
    }
    main p {
        font-size: 1rem;
    }
}

@media (max-width: 850px) {
    .tourism-container {
        height: 85vh;
        flex-direction: column-reverse;
        padding: 0.1rem 0;
    }
    .tourism-container .text {
        margin-bottom: 2%;
    }
    header h2 {
        font-size: 2.4rem;
    }
    main p {
        font-size: 1.2rem;
    }
    main .img-holder {
        display: none;
    }
}

@include mobile() {
    .tourism-container {
        padding: 1rem 0;
        height: 118vh;
    }
    .tourism-container .img-container::before {
        left: 0;
        top: 0;
        transform: scale(1.1);
    }
}
</style>

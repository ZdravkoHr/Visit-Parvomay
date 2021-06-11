<template>
    <nav class="main-nav">
        <div class="flex menu">
            <router-link to="home">Начало</router-link>

            <router-link to="places">Места</router-link>

            <router-link to="restaurants">Ресторанти</router-link>

            <router-link to="tourism">Туризъм</router-link>

            <router-link to="celebrations">Празненства</router-link>

            <router-link to="map">Карта</router-link>
        </div>
    </nav>
</template>

<style lang="scss" scoped>
.router-link-active {
    background: var(--clr-other-green);
}

.main-nav {
    background: #2e302d;
    position: sticky;
    top: 0;
    box-shadow: 0 0 0 0 rgba(0, 0, 0, 0.75);
    z-index: 999999;

    a {
        font-family: "Book Antiqua", Ariel;
        flex: 1;
        text-align: center;
        text-decoration: none;
        color: var(--clr-light-gray2);
        font-size: 2vw;
        padding: 2% 1.5%;
        display: inline-block;
        transition: ease-in-out 1s;

        &:hover {
            background: var(--clr-other-green);
            transition: 0.5s;
            cursor: pointer;
        }
    }

    a + a {
        border-left: 1px #61655a solid;
    }
}

@media (max-width: 500px) {
    .main-nav {
        display: none;
    }
}
</style>

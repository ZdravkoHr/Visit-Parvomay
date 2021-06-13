<template>
    <div class="box">
        <div class="image" :style="imgStyle"></div>
        <div class="text">
            <p class="title">{{ place.title }}</p>
            <p class="info">{{ place.info }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: ["place"],
    computed: {
        imgStyle() {
            return {
                backgroundImage: `url("${this.place.imgSrc}")`
            };
        }
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;
.image {
    background-size: cover;
    background-position: center;
    max-height: 300px;
    height: 30vw;
}

.text {
    background-color: var(--clr-light-gray2);
    color: #000;
    padding: 1rem 0.5rem;
}

.title {
    color: var(--clr-other-green);
    font-size: 1.2rem;
    margin-bottom: 5px;
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media(max-width: 1150px) {
    .image {height:25vw;}
}

@include mobile() {
    .title {
        font-size: 1rem;
    }

    .text {
        font-size: 0.8rem;
    }
}
</style>

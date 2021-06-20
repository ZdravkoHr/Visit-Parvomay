<template>
    <div class="comment-box" :style="commentBoxStyles">
        <div class="top-information">
            <p class="username">
                {{ info.user.name }}
            </p>
        </div>
        <div class="comment">
            <img
                :src="require(`@/assets/${info.user.img.path}`)"
                :alt="info.user.name"
                :style="userImgStyles"
            />

            <p class="heading">
                Коментар към: <b>{{ info.comment.place }}</b>
            </p>
            <p class="content">
                {{ info.comment.content }}
            </p>
        </div>
    </div>
</template>

<script>
export default {
    props: ["info"],
    computed: {
        commentBoxStyles() {
            return {
                "margin-top": this.halfSize,
                "margin-left": this.halfSize
            };
        },

        userImgStyles() {
            return {
                width: this.info.user.img.size + "px",
                transform: `translate(-${this.halfSize}, -${this.halfSize})`
            };
        },

        halfSize() {
            return this.info.user.img.size / 2 + "px";
        }
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;

.comment {
    background: var(--clr-light-gray1);
    border-radius: 10px;
    padding: 1rem;
}

.username {
    margin-left: 91px;
    color: #fff;
    font-weight: bold;
    font-size: 1.7rem;
    margin-bottom: 0.5rem;

    @media (max-width: 400px) {
        margin-left: 0;
    }
}

img {
    border-radius: 50%;
    overflow: hidden;
    float: left;
    shape-outside: polygon(
        53px 0px,
        90px 0px,
        53px 59px,
        -139px -123px,
        0px 0px
    );

    @media (max-width: 400px) {
        display: none;
    }
}

.heading {
    color: var(--clr-other-green);
    font-size: 20px;
    margin-bottom: 8px;

    @media (max-width: 400px) {
        text-align: center;
    }
}
</style>

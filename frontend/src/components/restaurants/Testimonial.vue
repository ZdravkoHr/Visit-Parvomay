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
            const halfSize = this.info.user.img.size / 2 + "px";
            return {
                "margin-top": halfSize,
                "margin-left": halfSize
            };
        },
        userImgStyles() {
            return {
                width: this.info.user.img.size + "px"
            };
        }
    }
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;
$img-size: 120px;

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
    transform: translate(-60px, -60px);
}

.heading {
    color: var(--clr-other-green);
    font-size: 20px;
    margin-bottom: 8px;
}

// .comment-box {
//     background: #f6f6f6;
//     border-radius: 10px;

//     p:last-child {
//         padding: 0 1.2rem 1.2rem;
//     }

//     .top-information {
//         display: flex;
//         flex-direction: row;
//         height: 20vh;
//         margin-top: -10vh;
//         div {
//             display: flex;
//             justify-content: space-around;
//             flex-direction: column;

//             p {
//                 margin-left: 6rem;
//                 font-size: 2rem;
//                 color: #62be9f;
//                 padding: 0;
//                 &:first-child {
//                     color: #f3f3f3;
//                     font-size: 1.7rem;
//                 }
//                 b {
//                     color: #609684;
//                 }
//                 span {
//                     color: #f3f3f3;
//                     margin-bottom: 3%;
//                     font-size: 1.7rem;
//                 }
//             }
//         }

//         .profile {
//             background-image: url("~@/assets/parvomay/User-Icon.png");
//             background-size: cover;
//             width: 7rem;
//             height: 7rem;
//             position: absolute;
//             border-radius: 50%;
//             margin-left: -3%;
//         }
//     }

//     @media (max-width: 1150px) {
//         .top-information div p:first-child {
//             font-size: 1.3rem;
//         }
//         .top-information div p:nth-child(2) {
//             font-size: 1.6rem;
//         }

//         p {
//             font-size: 0.8rem;
//         }
//     }

//     @media (max-width: 850px) {
//         .top-information {
//             margin-top: -9vh;
//             height: 17vh;
//             div p:nth-child(2) {
//                 font-size: 1.35rem;
//             }
//             div p:nth-child(1) {
//                 font-size: 1.1rem;
//             }
//         }
//         p:last-child {
//             padding: 1rem 1.2rem 1.2rem;
//         }
//     }

//     @media (max-width: 750px) {
//         .top-information div p:nth-child(2) {
//             font-size: 1.1rem;
//         }
//         .top-information div p:nth-child(1) {
//             font-size: 0.9rem;
//         }
//     }

//     @media (max-width: 650px) {
//         .top-information div p:nth-child(2) {
//             font-size: 1rem;
//             margin-left: 5rem;
//         }
//         .top-information div p:nth-child(1) {
//             font-size: 0.8rem;
//             margin-left: 5rem;
//         }
//         .top-information .profile {
//             width: 5rem;
//             height: 5rem;
//         }
//         .top-information {
//             margin-top: -4vh;
//             height: 13vh;
//         }
//     }

//     @include mobile() {
//         .top-information div p:nth-child(1),
//         .top-information div p:nth-child(2) {
//             margin-left: 5%;
//         }
//         .top-information .profile {
//             display: none;
//         }
//         p:last-child {
//             padding-top: 0.5rem;
//         }
//         & {
//             width: 90%;
//         }
//     }
// }
</style>

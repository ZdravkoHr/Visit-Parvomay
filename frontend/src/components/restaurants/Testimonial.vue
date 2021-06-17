<template>
    <div class="comment-box">
        <div class="top-information">
            <div>
                <p>{{ info.user.name }}</p>
                <p>
                    Коментар към: <b>{{ info.comment.place }}</b>
                </p>
            </div>
        </div>
        <p>
            {{ info.comment.content }}
        </p>
    </div>
</template>

<script>
export default {
    props: ["info"]
};
</script>

<style lang="scss" scoped>
@use '~@/styles/partials/mixins' as *;
.comment-box {
    background: #f6f6f6;
    border-radius: 10px;

    p:last-child {
        padding: 0 1.2rem 1.2rem;
    }

    .top-information {
        display: flex;
        flex-direction: row;
        height: 20vh;
        margin-top: -10vh;
        div {
            display: flex;
            justify-content: space-around;
            flex-direction: column;

            p {
                margin-left: 6rem;
                font-size: 2rem;
                color: #62be9f;
                padding: 0;
                &:first-child {
                    color: #f3f3f3;
                    font-size: 1.7rem;
                }
                b {
                    color: #609684;
                }
                span {
                    color: #f3f3f3;
                    margin-bottom: 3%;
                    font-size: 1.7rem;
                }
            }
        }

        .profile {
            background-image: url("~@/assets/parvomay/User-Icon.png");
            background-size: cover;
            width: 7rem;
            height: 7rem;
            position: absolute;
            border-radius: 50%;
            margin-left: -3%;
        }
    }

    @media (max-width: 1150px) {
        .top-information div p:first-child {
            font-size: 1.3rem;
        }
        .top-information div p:nth-child(2) {
            font-size: 1.6rem;
        }

        p {
            font-size: 0.8rem;
        }
    }

    @media (max-width: 850px) {
        .top-information {
            margin-top: -9vh;
            height: 17vh;
            div p:nth-child(2) {
                font-size: 1.35rem;
            }
            div p:nth-child(1) {
                font-size: 1.1rem;
            }
        }
        p:last-child {
            padding: 1rem 1.2rem 1.2rem;
        }
    }

    @media (max-width: 750px) {
        .top-information div p:nth-child(2) {
            font-size: 1.1rem;
        }
        .top-information div p:nth-child(1) {
            font-size: 0.9rem;
        }
    }

    @media (max-width: 650px) {
        .top-information div p:nth-child(2) {
            font-size: 1rem;
            margin-left: 5rem;
        }
        .top-information div p:nth-child(1) {
            font-size: 0.8rem;
            margin-left: 5rem;
        }
        .top-information .profile {
            width: 5rem;
            height: 5rem;
        }
        .top-information {
            margin-top: -4vh;
            height: 13vh;
        }
    }

    @include mobile() {
        .top-information div p:nth-child(1),
        .top-information div p:nth-child(2) {
            margin-left: 5%;
        }
        .top-information .profile {
            display: none;
        }
        p:last-child {
            padding-top: 0.5rem;
        }
        & {
            width: 90%;
        }
    }
}
</style>

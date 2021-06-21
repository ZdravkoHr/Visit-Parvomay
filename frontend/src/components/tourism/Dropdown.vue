<template>
    <div class="dropdown-container">
        <header @click="opened = !opened" :style="headerStyle">
            <h2>Релеф и климат</h2>
            <i class="fas fa-chevron-up" v-if="opened"></i
            ><i class="fas fa-chevron-down" v-if="!opened"></i>
        </header>
        <transition name="slide-in">
            <main v-if="opened">
                <div class="img-holder">
                    <img src="../../assets/tourism-example.jpg" alt="" />
                </div>
                <p class="p-1">
                    Lorem ipsum dolor sit amet consectetur adipisicing elit.
                    Iusto odio expedita, impedit eligendi hic in. Eligendi
                    doloremque tempore repudiandae quas eaque debitis dolorem
                    modi omnis, voluptate sequi. Doloribus cum perferendis
                    soluta impedit totam saepe harum non omnis quaerat enim,
                    odio nostrum nam suscipit qui est esse ut alias expedita quo
                    assumenda aspernatur repudiandae molestiae! Fuga reiciendis
                    quis eveniet laborum numquam?
                </p>
            </main>
        </transition>
    </div>
</template>
<script>
export default {
    data() {
        return {
            opened: false
        };
    },
    computed: {
        headerStyle() {
            return {
                "background-color": this.opened ? "#1c3637" : "#0e6749"
            };
        }
    }
};
</script>

<style lang="scss" scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #f3f3f3;
    padding: 20px;
    cursor: pointer;
    transition: ease-in-out 0.5s;
    &:hover {
        background-color: #1c3637 !important;
    }
    h2 {
        font-weight: 100;
        font-size: 30px;
    }
    i {
        font-size: 40px;
    }
}
main {
    display: flex;
    border: 1px solid #ccc;
    .img-holder {
        flex: 0.5;
        flex-basis: 50px;
    }
    p {
        flex: 2;
    }
}

/* ----------------------------------------------------------------------------
 -------------------------------- RESPONSIVE ----------------------------------
 ------------------------------------------------------------------------------ */

@media (max-width: 850px) {
    main .img-holder {
        display: none;
    }
}
</style>

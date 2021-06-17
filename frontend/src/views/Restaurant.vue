<template>
    <main-nav></main-nav>
    <main-header></main-header>
</template>
<script>
import Header from "@/components/header/Header";
import Navbar from "@/components/header/Navbar";

export default {
    components: {
        mainHeader: Header,
        mainNav: Navbar
    }
};
</script>

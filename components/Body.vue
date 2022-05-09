<template>
    <div>
        <Header/>
        <Contentone/>
        <Contenttwo/>
        <Contentthree/>
        <Contentfour/>
    </div>
</template>

<script>
import Header from './body-comp/header.vue'
import Contentone from './body-comp/content1.vue'
import Contenttwo from './body-comp/content2.vue'
import Contentthree from './body-comp/content3.vue'
import Contentfour from './body-comp/content4.vue'
import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
    components: {
        Header,
        Contentone,
        Contenttwo,
        Contentthree,
        Contentfour,
    },
}
</script>
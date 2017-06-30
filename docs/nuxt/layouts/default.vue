<template>
    <div class="bd-home">
        <m-nav></m-nav>
        
        <div class="main">
          <nuxt/>
        </div>

        <m-footer></m-footer>
    </div>
</template>

<script>
    import mNav from '../includes/nav.vue';
    import mFooter from '../includes/footer.vue';

    export default {
        components: {mNav, mFooter}
    };
</script>

<template>
    <container>
        <template v-slot:header>
            <h2>Local Storage</h2>
        </template>
    </container>
</template>
<script>
import Container from './Container.vue'
export default {
  components: { Container },
    name:"Header"
}
</script>
<style>
    .header{
        background-color: #c9252c;
        color: #fff;
        font-size: 26px;
        padding: 30px 0
    }
</style>
<template>
    <div class="container">
        <header class="header">
            <slot name="header"></slot>
        </header>
        <main class="main"></main>
        <footer class="footer"></footer>
    </div>
</template>
<script>
export default {
    name:"Container"
}
</script>
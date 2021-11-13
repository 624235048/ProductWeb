<template>
<nav class="navbar navbar-expand-lg navbar-light bg-light" style="height:70px">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">Product</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarColor03" aria-controls="navbarColor03" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarColor03">

        </div>
        <div class="navbar-nav mx-auto  justify-content-center w-50 order-1">
            <form class="form-inline">
            </form>

        </div>
        
    </div>
</nav>
</template>

<script>
export default {
    name: "HeaderProduct",
    methods: {
        
    },
    data() {
        return {
            search: ''
        }
    },
}
</script>

<style scoped>
.book-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}
</style>

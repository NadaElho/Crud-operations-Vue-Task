<script setup>
    import Header from './components/Header.vue'
    import Body from './components/Body.vue'
    import Sidebar from './components/Sidebar.vue'
    import Footer from './components/Footer.vue'
</script>
<template>
    <div class="container overflow-hidden text-center mt-2">
        <Header/>
        <div class="row p-2 justify-content-between">
            <div class="col-4">
               <Sidebar/>
            </div>
            <div class="col-8">
                <Body/>
            </div>
            <Footer/>
        </div>
    </div>
</template>
<style>
    
</style>
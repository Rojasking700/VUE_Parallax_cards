<template>
    <div class="parallax" >
        <img :src="pic.src" :id="pic.title" />
    </div>
</template>

<script>
export default {
    name: 'parallax',
    props:['pic']
}
</script>

<style>

</style>
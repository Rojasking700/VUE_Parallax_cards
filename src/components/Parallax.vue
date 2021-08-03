<template>
    <div class="parallax" >
        <div > 
            <img :src="pic.src" :id="pic.title" />
        </div>
        
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
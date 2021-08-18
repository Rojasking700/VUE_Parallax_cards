<template>
    <div class="card">
        <div class="circle"></div>
        <div class="content">
            <h2>Pepsi Cola</h2>
            <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. 
                Alias fugiat in neque blanditiis molestiae similique 
                consequatur maxime dolorum, hic nostrum?</p>
                <a href="#">Buy Now</a>
        </div>
        <img src="../assets/can-pepsi.png" class="image">
    </div>

</template>

<script>
export default {
    
}
</script>


<style>

    .card {
        position: absolute;
        width: 600px;
        height: 350px;
        /* background: #ccc; */
        border-radius: 20px;
        display: flex;
        align-items: center;
        border-radius: 20px;
        transition: 0.5s;
    }

    .card .circle {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 20px;
        overflow: hidden;
    }

    .card .circle::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: #d83133;
        clip-path:circle(120px at center);
        transition: 0.5s;
    }

    .card:hover .circle:before
    {
        background: #0065c3;
        clip-path:circle(400px at center);  
    }
    
    .card img {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        height: 300px;
        pointer-events: none;
        transition: 0.5s;
    }

    .card:hover img{
        left: 72%;
        height: 500px;

    }

    .card .content {
        position: relative;
        left: 20%;
        width: 50%;
        padding: 20px 20px 20px 40px;
        transition: 0.1s;
        pointer-events: none;
        visibility: hidden;
    }

    .card:hover .content{
        Left: 0;
        opacity: 1;
        visibility: visible;
    }

    .card .content h2{
        color: #fff;
        text-transform: uppercase;
        font-size: 2em;
        line-height: 1em;
        margin-bottom: 10px;
    }

    .card .content p {
        color: #fff;
    }

    .card .content a {
        position: relative;
        color: #fff;
        padding: 10px 20px;
        border-radius: 10px;
        background: #fff;
        color: #111;
        margin-top: 10px;
        display: inline-block;
        text-decoration: none;
        font-weight: 700;
    }


    @media (max-width: 800px){
        .card {
            width: auto;
            max-width: 350px;
            align-items: flex-start;
            /* margin: 10vh; */
        }

        .card:hover {
            height: 600px;
        }

        .card .content{
            width: 100%;
            left: 0;
            padding: 30px;
        }

        .card:hover img{
            top: 70%;
            left: 50%;
            height: 300px;
        }
    }
</style>
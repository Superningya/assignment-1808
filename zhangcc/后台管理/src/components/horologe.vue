<template>
     <div class="clock">
                <div class="hour" :style="{transform: 'rotate('+hourDeg+'deg)'}"></div>
                <div class="minute" :style="{transform: 'rotate('+minuteDeg+'deg)'}"></div>
                <div class="second" :style="{transform: 'rotate('+secondDeg+'deg)'}"></div>
                <ul>
                    <li v-for="item in 12" :style="{transform: 'rotate('+item*30+'deg)'}">{{item}}</li>
                </ul>
                <ol>
                    <li v-for="item in 60" :style="{transform: 'rotate('+item*6+'deg)'}"><i></i></li>
                </ol>
            </div>
</template>
<script>
export default {
    data(){
            return {
                hourDeg:new Date().getHours()*30+(new Date().getMinutes()/60*30),
                minuteDeg:new Date().getMinutes()*6+(new Date().getSeconds()/60*6),
                secondDeg: new Date().getSeconds()*6
            }
        },
        created(){
            this.dida();
        },
        methods:{
            dida(){
                setInterval(()=>{
                    this.hourDeg=new Date().getHours()*30+(new Date().getMinutes()/60*30),
                    this.minuteDeg=new Date().getMinutes()*6+(new Date().getSeconds()/60*6),
                    this.secondDeg=new Date().getSeconds()*6
                },1000)
            }
        }
}
</script>

<style>
    .clock{
        width: 500px;
        height: 500px;
        border-radius: 50%;
        border: 10px solid;
        margin: 50px auto;
        position: relative;
    }
    .clock::before{
        content: '';
        display: inline-block;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        background-color: #000;
        position: absolute;
        left: 50%;top: 50%;
        margin-left: -10px;
        margin-top: -10px;
        z-index: 1;
    }
    .clock .hour{
        position: absolute;
        width: 10px;
        height: 180px;
        background-color: #000;
        left: 50%;
        margin-left: -5px;
        top: 70px;
        transform-origin: center bottom;
    }
    .clock .minute{
        position: absolute;
        width: 8px;
        height: 200px;
        background-color: blue;
        left: 50%;
        margin-left: -4px;
        top: 50px;
        transform-origin: center bottom; 
    }
    .clock .second{
        position: absolute;
        width: 6px;
        height: 220px;
        background-color: red;
        left: 50%;
        margin-left: -3px;
        top: 30px;
        transform: rotateZ(6deg);
        transform-origin: center bottom; 
    }
    .clock ul li{
        width: 30px;
        height: 100%;
        padding-top: 17px;
        box-sizing: border-box;
        position: absolute;
        left: 50%;
        margin-left: -15px;
        top: 0;
        text-align: center;
    }
    .clock ol li{
        width: 4px;
        height: 100%;
        position: absolute;
        margin-bottom: 240px;
        left: 50%;
        margin-left: -2px;
        top: 0;
    }
    .clock ol li i{
        float: left;
        height: 10px;
        width: 100%;
        background-color: #000;
    }
    .clock ol li:nth-of-type(5n-5) i {
        height: 20px;
    }
</style>

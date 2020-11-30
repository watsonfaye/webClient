<template>
    <div id="top-bar">
        <div class="city-btn">{{selectedCity}}
            <div class="city-panel">
                <ul >
                    <li v-for="c in citys" :key="c.id" @click="selectedCity=c.cityname"><a href="#">{{c.cityname}}</a></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CompA",
        created:function () {
            let param=new URLSearchParams();
            param.append("opt","city");
            this.axios.post("/api/tw/home",param).then(d=>{
                this.citys=d.data;
            }).catch(d=>{
                alert(d);
            })
        },
        data:function () {
            return{
                citys:[],
                selectedCity:'城市'
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../sass/mixin";
    #top-bar{
        padding-left: 300px;
        width: 100%;
        background-color: darkgray;
        text-align: center;
        .city-btn{
            position: relative;
            display: block;
            @include button-normal;
            box-sizing: border-box;
            background-color: white;
            z-index: 2;
            &:hover{
                border-bottom: transparent;
                background-color: aquamarine;
                /*&+.city-panel{*/
                /*    display: block;*/
                /*}*/
                .city-panel{
                    z-index: 0;
                    display: block;
                }
            }

        }
        /*.city-panel:hover{*/
        /*    display: block;*/
        /*    &~.city-btn{*/
        /*        border-bottom: transparent;*/
        /*        background-color: aquamarine;*/
        /*    }*/
        /*}*/
        .city-panel{
            padding: 15px 15px  ;
            display: inline-block;
            position: relative;
            left: -1px;
            margin-top: -20px;
            //@include rect(300,450);
            width: 400px;
            @include bord();
            background-color: aquamarine;
            z-index: -1;
            display: none;
            ul{
                /*background-color: rebeccapurple;*/
                display: flex;
                flex-wrap: wrap;
                //justify-content: center;
                align-content: center;
                li{
                    width: 50px;
                    height: 30px;
                    /*background-color: red;*/
                    margin-right: 15px;
                    a{
                        text-decoration: none;
                    }
                }
            }
        }
    }
</style>
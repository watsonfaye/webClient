<template>
    <div id="d1">
        <div class="d2">D2</div>
        <div class="d3">D3</div>
        <div class="d4">D4</div>
        <div class="d5">D5</div>
        <div class="d6">D6</div>
        <div class="d7">D7</div>
    </div>
</template>

<script>
    export default {
        name: "ComB"
    }
</script>

<style lang="scss" scoped>
    @import "../sass/mixin";
    #d1{
        display: flex;
        flex-direction: row;//方向 默认row row-reverse column column-reverse
        flex-wrap: wrap;//控制是否换行 nowrap 不换行 wrap=reverse 从上往下换行
        /*flex-flow: row-reverse wrap;*/
        justify-content: center;//水平布局
        background-color: skyblue;
        align-items: flex-start;//垂直布局
        align-content: space-around;
        @include rect(350,350)
    }
    .d2,.d3,.d4,.d5,.d6,.d7{
        text-align: center;
        line-height: 100px;
        @include rect(100,100);
        background-color: yellow;
        @include bord();
    }
</style>
<template>
    <div>
        <header>
            <h1>大数据可视化</h1>
        </header>
        <section class="container">
            <section class="itemLeft">
                <item-page>
                    <item-one></item-one>
                </item-page>
                <item-page>
                    <item-two></item-two>
                </item-page>
            </section>
            <section class="itemCenter">
                <map-page></map-page>
            </section>
            <section class="itemRight">
                <item-page>
                    <item-three></item-three>
                </item-page>
                <item-page>
                    <item-four></item-four>
                </item-page>
            </section>
        </section>
        
    </div>
</template>

<script>
import itemPage from '@/components/itemPage.vue'
import itemOne from '@/components/itemOne.vue'
import itemTwo from '@/components/itemTwo.vue'
import itemThree from '@/components/itemThree.vue'
import itemFour from '@/components/itemFour.vue'
import mapPage from '@/components/mapPage.vue'

import {inject} from 'vue'
    export default {
        components: {itemPage,itemOne,itemTwo,itemThree,itemFour,mapPage},
        setup(){
            let $echarts = inject("echarts")
            let $http = inject("axios")
            console.log("echarts===", $echarts)
            console.log("axios===", $http)
        }    
    }
</script>


<style lang="less">

header{
    height: 1rem;
    width: 100%;
    background-color: rgba(0 , 0 ,255, 0.2);
    h1 {
        font-size: 0.375rem;
        color: #FFF;
        text-align: center;
        line-height: 1rem;
    }
}
.container{
    min-width: 1200px;
    max-width: 2048px;
    margin: 0 auto;
    padding: .125rem .125rem 0;
    // border: 1px solid red;
    display: flex;
    .itemLeft, .itemRight{
        flex: 3;
    }
    .itemCenter{
        flex: 5;
        height: 10.5rpx;
        // border: 1px solid blue;
        padding: 0.125rem;
        margin: .25rem;
    }
}
</style>



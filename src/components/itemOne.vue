<template>
    <div>
        <h2>图表</h2>
        <div class="chart" id="oneChart">
            图表的容器
        </div>
    </div>
</template>

<script>
    import {inject,onMounted,reactive} from 'vue'

    export default {
        setup(){
            let $echarts = inject("echarts")
            let $http = inject("axios")

            let data = reactive({})
            let xdata = reactive([])
            let ydata = reactive([])

            async function getData() {
                data = await $http({url:"/one/data",})
                console.log("oneData", data.data.chartOne.chartData)
            }

            function setData() {
                xdata = data.data.chartOne.chartData.map(v => v.title)
                ydata = data.data.chartOne.chartData.map(v => v.num)
                console.log("xdata", xdata, "ydata", ydata)
            }

            onMounted(() => {
                let myChart =  $echarts.init(document.getElementById("oneChart"))

                getData().then(() => {
                    setData();
                    myChart.setOption({
                        grid:{
                            top:"3%",
                            left:"1%",
                            right:"6%",
                            bottom:"3%",
                            containLabel: true
                        },
                        xAxis:{
                            type:"value",
                            axisLine:{
                                lineStyle:{
                                    color:'black'
                                }
                            }
                        },
                        yAxis:{
                            type:"category",
                            axisLine:{
                                lineStyle:{
                                    color:'black'
                                }
                            },
                            data:xdata
                        },
                        series:[
                            {
                                type:"bar",
                                data:ydata,
                                itemStyle: {
                                    normal: {
                                        barBorderRadius:[0,20,20,0],    //设置柱状的圆角
                                        color: new $echarts.graphic.LinearGradient(0,0,1,0 ,[
                                            {
                                                offset: 0,
                                                color: "#005eaa",
                                            },
                                            {
                                                offset: 0.5,
                                                color: "#339ca8",
                                            },
                                            {
                                                offset: 1,
                                                color: "#cda819",
                                            }
                                        ])
                                    }
                                }
                            }
                        ],
                    })
                })
            })

            return{
                getData,
                data,
                xdata,
                ydata,
                setData
            }
        }
    }
</script>

<style lang="less" scoped>
.chart{
    height: 4.5rem
}
h2{
    height: .6rem;
    color:white;
    line-height: 0.6rem;
    font-size: 0.25rem;
    text-align:center;
}
</style>
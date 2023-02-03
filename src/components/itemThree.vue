<template>
    <div>
        <h2>库存统计</h2>
        <div class="chart" id="pieChart"></div>
    </div>
</template>

<script>
    import {inject,onMounted,reactive} from 'vue'

    export default {
        setup(){
            let $echarts = inject('echarts')
            let $http = inject('axios')

            let data = reactive({})

            async function getData(){
                data = await $http({url:"/three/data"})
            }

            onMounted(() => {
                getData().then(() => {
                    console.log("饼状图数据", data)
                    let myChart = $echarts.init(document.getElementById("pieChart"))

                    myChart.setOption({
                        // 设置图例
                        legend: {
                            top: "bottom",
                        },
                        // 提示框
                        tooltip: {
                            show: true,
                        },
                        series: [
                            {
                            type: "pie", // 类型为饼状图
                            data: data.data.chartThree.chartData,
                            radius: [10, 100],
                            center: ["50%", "45%"],
                            roseType: "area",
                            itemStyle: {
                                borderRadius: 10,
                            },
                            },
                        ],
                    })
                })
            })

            return{
                data,
                getData
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
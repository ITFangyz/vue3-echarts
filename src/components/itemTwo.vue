<template>
    <div>
        <h2>月销图</h2>
        <div class="chart" id="monthChart">
        </div>
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
                data = await $http({url:"/two/data"})
            }

            onMounted(() => {
                getData().then(() => {
                    console.log("月销图数据", data)
                    let myChart = $echarts.init(document.getElementById("monthChart"))

                    myChart.setOption({
                        tooltip: {
                            trigger: "axios",
                            // 十字指向器
                            axisPointer: {
                            type: "cross",
                            label: {
                                backgroundColor: "#e6b600",
                            },
                            },
                        },
                        grid: {
                            left: "1%",
                            right: "4%",
                            bottom: "3%",
                            containLabel: true,
                        },
                        legend: {
                            data: ["服饰", "数码产品", "家电", "家居", "日化"],
                        },
                        xAxis: {
                            type: "category",
                            boundaryGap: false,
                            data: data.data.chartTwo.chartData.day,
                            axisLabel: {
                            show: true,
                            textStyle: {
                                color: "#fff",
                            },
                            },
                        },
                        yAxis: {
                            type: "value",
                            axisLabel: {
                            show: true,
                            textStyle: {
                                color: "#fff",
                            },
                            },
                        },
                        series: [
                            {
                            type: "line", // 类型为折线图
                            name: "服饰",
                            data: data.data.chartTwo.chartData.num.Clothes,
                            smooth: true, // 平滑过渡
                            showSymbol: false, // 隐藏点
                            stack: "Total", // 开启堆叠
                            lineStyle: {
                                width: 0,
                            },
                            // 选中的高亮
                            emphasis: {
                                focus: "series",
                            },
                            areaStyle: {
                                // 区域颜色填充
                                opacity: 0.8, // 透明度
                                // 设置渐变色
                                color: new $echarts.graphic.LinearGradient(0, 0, 0, 1, [
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
                                    color: "#bca119",
                                },
                                ]),
                            },
                            },
                            {
                            type: "line", // 类型为折线图
                            name: "数码产品",
                            data: data.data.chartTwo.chartData.num.Electrical,
                            smooth: true, // 平滑过渡
                            showSymbol: false, // 隐藏点
                            stack: "Total", // 开启堆叠
                            lineStyle: {
                                width: 0,
                            },
                            // 选中的高亮
                            emphasis: {
                                focus: "series",
                            },
                            areaStyle: {
                                // 区域颜色填充
                                opacity: 0.8, // 透明度
                                // 设置渐变色
                                color: new $echarts.graphic.LinearGradient(0, 0, 1, 0, [
                                {
                                    offset: 0,
                                    color: "#01cd89",
                                },
                                {
                                    offset: 0.5,
                                    color: "#339ca8",
                                },
                                {
                                    offset: 1,
                                    color: "#cba876",
                                },
                                ]),
                            },
                            },
                            {
                            type: "line", // 类型为折线图
                            name: "家电",
                            data: data.data.chartTwo.chartData.num.digit,
                            smooth: true, // 平滑过渡
                            showSymbol: false, // 隐藏点
                            stack: "Total", // 开启堆叠
                            lineStyle: {
                                width: 0,
                            },
                            // 选中的高亮
                            emphasis: {
                                focus: "series",
                            },
                            areaStyle: {
                                // 区域颜色填充
                                opacity: 0.8, // 透明度
                                // 设置渐变色
                                color: new $echarts.graphic.LinearGradient(0, 0, 1, 0, [
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
                                    color: "#cda231",
                                },
                                ]),
                            },
                            },
                            {
                            type: "line", // 类型为折线图
                            name: "日化",
                            data: data.data.chartTwo.chartData.num.gear,
                            smooth: true, // 平滑过渡
                            showSymbol: false, // 隐藏点
                            stack: "Total", // 开启堆叠
                            lineStyle: {
                                width: 0,
                            },
                            // 选中的高亮
                            emphasis: {
                                focus: "series",
                            },
                            areaStyle: {
                                // 区域颜色填充
                                opacity: 0.8, // 透明度
                                // 设置渐变色
                                color: new $echarts.graphic.LinearGradient(0, 0, 1, 0, [
                                {
                                    offset: 0,
                                    color: "#0eaa06",
                                },
                                {
                                    offset: 0.5,
                                    color: "#399ba3",
                                },
                                {
                                    offset: 1,
                                    color: "#cb3a6c",
                                },
                                ]),
                            },
                            },
                            {
                            type: "line", // 类型为折线图
                            name: "家居",
                            data: data.data.chartTwo.chartData.num.Chemicals,
                            smooth: true, // 平滑过渡
                            showSymbol: false, // 隐藏点
                            stack: "Total", // 开启堆叠
                            lineStyle: {
                                width: 0,
                            },
                            // 选中的高亮
                            emphasis: {
                                focus: "series",
                            },
                            areaStyle: {
                                // 区域颜色填充
                                opacity: 0.8, // 透明度
                                // 设置渐变色
                                color: new $echarts.graphic.LinearGradient(0, 0, 1, 0, [
                                {
                                    offset: 0,
                                    color: "#055aba",
                                },
                                {
                                    offset: 0.5,
                                    color: "#312ad2",
                                },
                                {
                                    offset: 1,
                                    color: "#cac349",
                                },
                                ]),
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
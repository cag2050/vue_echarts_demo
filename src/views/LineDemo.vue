<template>
    <div>
        <div class="chart_container">
            <v-chart :options="options" :autoresize="true" />
        </div>
    </div>
</template>

<script>
import ECharts from "vue-echarts"
import "echarts/lib/chart/line"
import "echarts/lib/component/title"
import "echarts/lib/component/grid"
import "echarts/lib/component/legend"
import "echarts/lib/component/tooltip"
import "echarts/lib/component/dataZoom"
import "echarts/lib/component/toolbox"

export default {
    components: {
        "v-chart": ECharts
    },
    data() {
        return {
            options: {
                title: {
                    text: "未来一周气温变化"
                },
                xAxis: {
                    type: "category",
                    data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
                    axisTick: {
                        alignWithLabel: true
                    }
                },
                series: [
                    {
                        data: [820, 932, 901, 934, 1290, 1330, 1320],
                        type: "line",
                        smooth: false
                    }
                ],
                yAxis: {
                    type: "value"
                },
                toolbox: {
                    right: 50,
                    feature: {
                        dataZoom: {
                            yAxisIndex: "none"
                        },
                        restore: {},
                        saveAsImage: {}
                    }
                },
                tooltip: {
                    trigger: "axis"
                },
                grid: {
                    left: 70,
                    right: 50
                },
                dataZoom: [
                    {
                        type: "inside",
                        start: 0,
                        end: 100
                    },
                    {
                        start: 0,
                        end: 10,
                        handleIcon:
                            "M10.7,11.9v-1.3H9.3v1.3c-4.9,0.3-8.8,4.4-8.8,9.4c0,5,3.9,9.1,8.8,9.4v1.3h1.3v-1.3c4.9-0.3,8.8-4.4,8.8-9.4C19.5,16.3,15.6,12.2,10.7,11.9z M13.3,24.4H6.7V23h6.6V24.4z M13.3,19.6H6.7v-1.4h6.6V19.6z",
                        handleSize: "80%",
                        handleStyle: {
                            color: "#fff",
                            shadowBlur: 3,
                            shadowColor: "rgba(0, 0, 0, 0.6)",
                            shadowOffsetX: 2,
                            shadowOffsetY: 2
                        }
                    }
                ]
            }
        }
    },
    mounted() {},
    methods: {}
}
</script>

<style scoped>
.chart_container {
    width: 100%;
    height: 400px;
}
.echarts {
    width: 100%;
    height: 100%;
}
</style>

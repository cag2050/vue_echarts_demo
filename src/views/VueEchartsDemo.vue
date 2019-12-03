<template>
    <div>
        <div class="chart_container">
            <v-chart :options="polar" :autoresize="true" />
        </div>
    </div>
</template>

<script>
import ECharts from "vue-echarts"
import "echarts/lib/chart/line"
import "echarts/lib/component/polar"

export default {
    components: {
        "v-chart": ECharts
    },
    data() {
        return {
            polar: {
                title: {
                    text: "极坐标双数值轴"
                },
                legend: {
                    data: ["line"]
                },
                polar: {
                    center: ["50%", "54%"]
                },
                tooltip: {
                    trigger: "axis",
                    axisPointer: {
                        type: "cross"
                    }
                },
                angleAxis: {
                    type: "value",
                    startAngle: 0
                },
                radiusAxis: {
                    min: 0
                },
                series: [
                    {
                        coordinateSystem: "polar",
                        name: "line",
                        type: "line",
                        showSymbol: false,
                        data: []
                    }
                ],
                animationDuration: 2000
            }
        }
    },
    mounted() {
        for (let i = 0; i <= 360; i++) {
            let t = (i / 180) * Math.PI
            let r = Math.sin(2 * t) * Math.cos(2 * t)
            this.polar.series[0].data.push([r, i])
        }
    }
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

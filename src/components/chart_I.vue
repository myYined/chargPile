<template>
    <div id="chart-I"></div>
</template>

<script>
import * as echarts from "echarts"
export default {
    name: "chart_I",
    data() {
        return {
            colorList: ['#5470c6', '#91cc75', '#fac858', '#ee6666', '#73c0de', '#3ba272', '#fc8452', '#9a60b4', '#ea7ccc'],
            select: 0,
            option: {
                series: [
                    {
                        name: '访问来源',
                        type: 'pie',
                        radius: ['40%', '70%'],
                        avoidLabelOverlap: false,
                        itemStyle: {
                            borderRadius: 10,
                            borderColor: '#fff',
                            borderWidth: 2
                        },
                        // 高亮状态的扇区和标签样式(等同于选中)
                        emphasis: {
                            scale: false,
                            label: {
                                show: false
                            },
                            focus: "none"
                        },
                        markLine: {
                            silent: true
                        },
                        labelLine: {
                            show: true
                        },
                        label: {
                            show: false,
                            position: "center",
                            formatter: ` {b}\n\n{c}`
                        },
                        selectedMode: "single",
                        selectedOffset: 10,
                        select: {
                            label: {
                                show: true,
                                fontSize: 32,
                                fontWeight: "bolder"
                            },
                            itemStyle: {
                            }
                        },
                        data: [
                            {value: 1048, name: '搜索引擎', selected: false},
                            {value: 735, name: '直接访问', selected: false},
                        ],
                        animation: true
                        // animationType: "scale",
                        // animationEasing: "elasticOut"
                    }
                ]
            },
            chart: null,
            nameList: ["1", "2", "3", "4"],
            index: 0,
        }
    },
    mounted() {
        this.chartInitialization();
    },
    methods: {
        chartInitialization() {
            this.chart = echarts.init(document.getElementById("chart-I"));
            this.chart.setOption(this.option);
            this.changeSelect()
        },
        changeSelect() {
            //console.log(this.option.series[0].data)
            let {data} = this.option.series[0];
            for(let i = 0; i < data.length; i++) {
                data[i].selected = false;
            }
            console.log('select',this.select)
            data[this.select].selected = true;
            data[this.select].name = this.nameList[this.index]
            data[this.select].value = parseInt(Math.random()*3000 + 2000);
            console.log('data[0]',data[0].selected);
            console.log('data[1]',data[1].selected);
            this.select++;
            this.index++;
            if(this.index === this.nameList.length) {
                this.index = 0;
            }
            if(this.select === data.length) {
                this.select = 0;
            }
            setTimeout(()=> {
                console.log(this.option.series[0].data[0].selected);
                console.log(this.option.series[0].data[1].selected);
                this.chart.setOption(this.option);
                this.changeSelect()
            }, 6000);
        }
    }
}
</script>

<style scoped>
#chart-I {
    width: 100%;
    height: 500px;
}
</style>
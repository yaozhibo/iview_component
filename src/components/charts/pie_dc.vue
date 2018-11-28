<template>
    <div ref="dom" class="charts chart-pie-dc"></div>
</template>

<script>
    import echarts from 'echarts'
    import tdTheme from './theme.json'
    import { on, off } from '@/libs/tools'
    echarts.registerTheme('tdTheme', tdTheme)
    export default {
        name: 'ChartPieDc',
        props: {
            value: Array,
            text: String,
            subtext: String,
            name: String
        },
        data () {
            return {
                dom: null
            }
        },
        methods: {
            resize () {
                this.dom.resize()
            }
        },
        mounted () {
            this.$nextTick(() => {
                let legend = this.value.map(_ => _.name)
                let option = {
                    title: {
                        text: this.text,
                        subtext: this.subtext,
                        x: 'center'
                    },
                    tooltip: {
                        trigger: 'item',
                        formatter: '{a} <br/>{b} : {c} ({d}%)'
                    },
                    legend: {
                        orient: 'vertical',
                        left: 'left',
                        data: legend
                    },
                    series: [
                        {
                            name: this.name,
                            type: 'pie',
                            radius: ['50%', '70%'],
                            avoidLabelOverlap: false,
                            data: this.value,
                            label: {
                                normal: {
                                    show: false,
                                    position: 'center'
                                },
                                emphasis: {
                                    show: true,
                                    textStyle: {
                                        fontSize: '30',
                                        fontWeight: 'bold'
                                    }
                                }
                            },
                            labelLine: {
                                normal: {
                                    show: false
                                }
                            },
                        }
                    ]
                }
                this.dom = echarts.init(this.$refs.dom, 'tdTheme')
                this.dom.setOption(option)
                on(window, 'resize', this.resize)
            })
        },
        beforeDestroy () {
            off(window, 'resize', this.resize)
        }
    }
</script>
<template>
    <div ref="dom" class="charts chart-pie-np"></div>
</template>

<script>
    import echarts from 'echarts'
    import tdTheme from './theme.json'
    import { on, off } from '@/libs/tools'
    echarts.registerTheme('tdTheme', tdTheme)
    export default {
        name: 'ChartPieNp',
        props: {
            value: Array,
            value_1: Array,
            text: String,
            subtext: String,
            name: String
        },
        data() {
            return {
                dom: null
            }
        },
        methods: {
            resize() {
                this.dom.resize()
            }
        },
        mounted() {
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
                        data: this.legend
                    },
                    series: [
                        {
                            name: this.name,
                            type: 'pie',
                            selectedMode: 'single',
                            radius: [0, '30%'],
                            data: this.value_1,
                            label: {
                                normal: {
                                    position: 'inner'
                                }
                            },
                            labelLine: {
                                normal: {
                                    show: false
                                }
                            },
                        },
                        {
                            name: this.name,
                            type: 'pie',
                            radius: ['40%', '55%'],
                            label: {
                                normal: {
                                    formatter: '{a|{a}}{abg|}\n{hr|}\n  {b|{b}：}{c}  {per|{d}%}  ',
                                    backgroundColor: '#eee',
                                    borderColor: '#aaa',
                                    borderWidth: 1,
                                    borderRadius: 4,
                                    // shadowBlur:3,
                                    // shadowOffsetX: 2,
                                    // shadowOffsetY: 2,
                                    // shadowColor: '#999',
                                    // padding: [0, 7],
                                    rich: {
                                        a: {
                                            color: '#999',
                                            lineHeight: 22,
                                            align: 'center'
                                        },
                                        // abg: {
                                        //     backgroundColor: '#333',
                                        //     width: '100%',
                                        //     align: 'right',
                                        //     height: 22,
                                        //     borderRadius: [4, 4, 0, 0]
                                        // },
                                        hr: {
                                            borderColor: '#aaa',
                                            width: '100%',
                                            borderWidth: 0.5,
                                            height: 0
                                        },
                                        b: {
                                            fontSize: 16,
                                            lineHeight: 33
                                        },
                                        per: {
                                            color: '#eee',
                                            backgroundColor: '#334455',
                                            padding: [2, 4],
                                            borderRadius: 2
                                        }
                                    }
                                }
                            },
                            data: this.value
                        }
                    ],

                }
                this.dom = echarts.init(this.$refs.dom, 'tdTheme')
                this.dom.setOption(option)
                on(window, 'resize', this.resize)
            })
        },
        beforeDestroy() {
            off(window, 'resize', this.resize)
        }
    }
</script>
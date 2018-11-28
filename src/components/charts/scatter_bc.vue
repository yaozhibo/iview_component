<template>
    <div ref="dom" class="charts chart-scatter-bc"></div>
</template>

<script>
    import echarts from 'echarts'
    import tdTheme from './theme.json'
    import { on, off } from '@/libs/tools'
    echarts.registerTheme('tdTheme', tdTheme)
    export default {
        name: 'ChartScatterBc',
        props: {
            value: Array,
        },
        data () {
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
                let option = {
                    title: {
                        text: this.text,
                        subtext: this.subtext,
                        x: 'center'
                    },
                    series: [{
                        xAxis: {},
                        yAxis: {},
                        symbolSize: 20,
                        data: this.value
                    }],
                    type: 'scatter',

                };
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
<template>
  <div>
    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="8" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-scatter-bc style="height: 300px;" :value="scatterBcData" text="用户访问来源" subtext="英国"></chart-scatter-bc>
        </Card>
      </i-col>
    </Row>
  </div>
</template>
<script>
    import InforCard from '_c/info-card'
    import CountTo from '_c/count-to'
    import {ChartScatterBc} from '_c/charts'
    export default {
        name: 'scatter',
        components: {
            InforCard,
            CountTo,
            ChartScatterBc
        },
        data () {
            return  {
                scatterBcData: [
                    [10.0, 8.04],
                    [8.0, 6.95],
                    [13.0, 7.58],
                    [9.0, 8.81],
                    [11.0, 8.33],
                    [14.0, 9.96],
                    [6.0, 7.24],
                    [4.0, 4.26],
                    [12.0, 10.84],
                    [7.0, 4.82],
                    [5.0, 5.68]
                ]
            }
        }
    }

</script>
<style lang="less">
  .count-style{
    font-size: 50px;
  }
</style>
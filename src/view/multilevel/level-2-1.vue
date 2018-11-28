<template>
  <div>
    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="8" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-pie style="height: 300px;" :value="pieData" text="用户访问来源" subtext="英国"></chart-pie>
        </Card>
      </i-col>
      <i-col :md="24" :lg="8" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-pie-cp style="height: 300px;" :value="pieCpData" text="用户访问来源" subtext="法国" name="访问类型"></chart-pie-cp>
        </Card>
      </i-col>
      <i-col :md="24" :lg="8" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-pie-dc style="height: 300px;" :value="pieDcData" text="用户访问来源" subtext="美国" name="访问类型"></chart-pie-dc>
        </Card>
      </i-col>
    </Row>

    <Row :gutter="20" style="margin-top: 10px;">
      <i-col :md="24" :lg="10" style="margin-bottom: 20px;">
        <Card shadow>
          <chart-pie-np style="height: 300px;" text="用户访问来源" subtext="中国" name="访问类型" :value="pieNpData" :value_1="pieNpData1"></chart-pie-np>
        </Card>
      </i-col>
    </Row>

  </div>
</template>

<script>
    import InforCard from '_c/info-card'
    import CountTo from '_c/count-to'
    import { ChartPie, ChartBar, ChartPieCp, ChartPieDc, ChartPieNp} from '_c/charts'
    export default {
        name: 'pie',
        components: {
            InforCard,
            CountTo,
            ChartPie,
            ChartBar,
            ChartPieCp,
            ChartPieDc,
            ChartPieNp
        },
        data () {
            return {
                pieData: [
                    {value: 335, name: '直接访问'},
                    {value: 310, name: '邮件营销'},
                    {value: 234, name: '联盟广告'},
                    {value: 135, name: '视频广告'},
                    {value: 1548, name: '搜索引擎'}
                ],
                pieCpData: [
                    {value:556, name:'直接访问'},
                    {value:543, name:'邮件营销'},
                    {value:342, name:'联盟广告'},
                    {value:577, name:'视频广告'},
                    {value:345, name:'搜索引擎'}
                ],
                pieDcData: [
                    {value:234, name:'直接访问'},
                    {value:843, name:'邮件营销'},
                    {value:565, name:'联盟广告'},
                    {value:342, name:'视频广告'},
                    {value:888, name:'搜索引擎'}
                ],
                pieNpData: [
                    {value:335, name:'直达'},
                    {value:310, name:'邮件营销'},
                    {value:234, name:'联盟广告'},
                    {value:135, name:'视频广告'},
                    {value:1048, name:'百度'},
                    {value:251, name:'谷歌'},
                    {value:147, name:'必应'},
                    {value:102, name:'其他'}
                ],
                pieNpData1: [
                    {value:335, name:'直达', selected:true},
                    {value:679, name:'营销广告'},
                    {value:1548, name:'搜索引擎'}
                ]
            }
        },

        mounted () {

        },
    }
</script>

<style lang="less">
  .count-style{
    font-size: 50px;
  }
</style>

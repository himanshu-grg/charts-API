<template>
    <div>
        <Chart v-if="!isLoading" :date="date" :data1="data1" :data2="data2" :def="def"/>
    </div>
</template>

<script type="text/javascript">
    import axios from 'axios'
    import Chart from '../components/chart.vue'
    export default {
        name:'ContainerComp',
        components: {
            Chart
        },
        data () {
          return {
            date: [],
            data1:[],
            data2:[],
            def:[],
            isLoading: false
          }
        },
        methods: {
            async getData () {
                this.isLoading = true
                let result = await axios.get(`https://api.wirespec.dev/wirespec/stackoverflow/fetchchartdataforvuejs`)
                this.date = result.data.date
                //console.log(result.data)
                this.challenge = result.data.challenge
                this.isLoading = false
                const d1 =new Date()
                const d2 = new Date()
                d2.setMonth(d2.getMonth() +12)
                let d3 = d1.getTime()
                let d4 = d2.getTime()
                this.dates.push(d3)
                this.dates.push(d4)
            }
        },
        mounted () {
            this.getData()
        }
    }
</script>
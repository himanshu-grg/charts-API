<template>
  <div>
    <canvas id="mychart" width="550" height="300"></canvas>
    <button @click="changeLabel()">click</button>
  </div>
</template>

<script>

export default {
  name: 'Chart',
  props: ['date', 'data1', 'data2', 'def'],
  data: () => (
    {Chart_2:""},
    {portfolio1:""},
    {portfolio2:""},
    {total:''},
    {default:""},
    {labell:""},
    {dataaa:""},
    {i:0}
  ),
  methods : {
    changeLabel(){
      //this.Chart_2.destroy()
      let list= [this.portfolio1, this.portfolio2, this.total]
      let labels = ["Portfolio 1", "Portfolio 2", "Total"]
      this.Chart_2.data.datasets[0].data = list[this.i]
      this.Chart_2.data.datasets[0].label = labels[this.i]
      //this.labell = labels[this.i]
    //   console.log(this.i)
    //   console.log(this.labell)
    //   console.log(this.Chart_2.data.datasets[0].data)
      this.i= this.i + 1
      if(this.i==3){this.i=0}
      this.Chart_2.update()
      //this.makeGraph()
    },

    makeGraph(){
        this.portfolio1 = this.dates.map((dates, index) => ({
        x: new Date(dates),
        y: this.data1[index]
        }))
        this.portfolio2 = this.dates.map((dates, index) => ({
        x: new Date(dates),
        y: this.data2[index]
        }))
        this.total = this.dates.map((dates, index) => ({
        x: new Date(dates),
        y: this.data1[index] + this.data2[index] + this.challenge[index]
        }))
        this.default = this.dates.map((dates, index) => ({
        x: new Date(dates),
        y: this.def[index]
        }))
        const ctx = document.getElementById('mychart').getContext('2d')
        this.Chart_2 = new Chart(ctx, {
        type: 'line',
        data: {
            datasets: [
            {
                data: this.dataaa||this.default,
                label: this.labell || "Default",
                borderColor: '#F25207'
            }]
        },
        options: {
            scales: {
            xAxes: [
                {
                type: 'time',
                time: {
                    unit: 'month',
                    displayFormats: {
                    years: 'MMM YYYY'
                    }
                },
                gridLines: {
                    display: false
                }
                }
            ],
            yAxes: [{
                gridLines: {
                    display: true
                }
                }],
            //     ticks: {
            //       // eslint-disable-next-line no-unused-vars
            //       // callback (value, index, values) {
            //       //   return `${value}`
            //       // }

            //     }
            },
            legend: {
                display: true
            },
            responsive: true,
            maintainAspectRatio: false
        }
        })
    }
  },
  mounted () {
    this.makeGraph()    
  }
}
</script>
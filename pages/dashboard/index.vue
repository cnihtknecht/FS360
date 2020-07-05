<template>
    <div class="flex flex-col">
        <contentCard class="mt-2 mb-4">
            <template v-slot:title>
                SALES STATISTICS
            </template>
            <template v-slot:content>
                <div class="w-full overflow-hidden p-2">
                    <barChart :chart-data="revenueMonthly.barChartData" 
                    :options="revenueMonthly.barChartOptions" :height="120"></barChart>
                </div>
            </template>


        </contentCard>   
    </div>
</template>

<script>
import ContentCard from "~/components/items/ContentCard.vue";
import BarChart from '~/components/charts/Barchart';
import LineChart from '~/components/charts/LineChart';

const chartColors = {
red: 'rgb(255, 99, 132)',
orange: 'rgb(255, 159, 64)',
yellow: 'rgb(255, 205, 86)',
green: 'rgb(75, 192, 192)',
blue: 'rgb(54, 162, 235)',
purple: 'rgb(153, 102, 255)',
grey: 'rgb(201, 203, 207)'
};

    export default {
        transition:{
            name:"inventory",
            mode:"out-in",
            duration: {enter:1000, leave:500},
            enterActiveClass: "animated fadeIn",
            leaveActiveClass: "animated fadeOut"
        },

        layout: "dashboard",   //uses the ~/layouts/dashboard.vue instead of default.vue
        components:{
            ContentCard,
            BarChart,
            LineChart
        },
        
        data(){
            return{
                revenueMonthly:{
                    barChartData: {
                        labels:['Jan','Feb', 'Mar', 'Apr', 'May','Jun','Jul','Aug'],
                        datasets: [
                        {
                            label: 'Income',
                            //barThickness: 25,
                            backgroundColor: [
                                chartColors.green,
                                chartColors.red,
                                chartColors.blue,
                                chartColors.purple,
                                chartColors.grey,
                                chartColors.yellow,
                                chartColors.orange,
                                chartColors.red
                                ],
                            //data: [512, 300, 443, 605, 400, 239, 343, 776]
                            data: [{x:'2016-12-20', y:20}, {x:'2016-12-21', y:10},
                            {x:'2016-12-22', y:30},{x:'2016-12-23', y:23},
                            {x:'2016-12-24', y:53},{x:'2016-12-25', y:47},
                            {x:'2016-12-26', y:12},{x:'2016-12-27', y:18}]

                        }   
                        ],    
                    },
                    barChartOptions: {
                        responsive: true,
                        legend: {
                            display: false,
                        },
                        title: {
                            display: true,
                            text: 'Monthly Income'
                        },
                        scales: {
                            yAxes: [
                                {
                                    offset: false,
                                    ticks: {
                                        beginAtZero: true,
                                        suggestedMax: 10
                                    }
                                }
                            ]
                        }
                    }
                }
            }
        },
    }
</script>
<template>
  <q-card class="sale-analytics w-sales">
    <q-card-section class="tatal-sales">
      <div class="tatal-head">
        <h2>Weekly Sales</h2>
        <h3>Total 85.4k Sales</h3>
      </div>
      <div class="kabab-menu">
        <svg style="width: 24px;height: 24px;">
          <path fill="currentColor"
                d="M12 16a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2Z"></path>
        </svg>
      </div>
    </q-card-section>
    <q-card-section class="sale-graph">
      <vue-apex-charts
          :options="chartOptions"
          :series="series"
          height="250px"
      ></vue-apex-charts>
    </q-card-section>
    <q-card-section class="sale-profit">
      <div class="sale-des">
        <div class="sales-icon icon">
          <svg style="width: 24px;height: 24px;margin: 10px 0px;">
            <path fill="currentColor"
                  d="m16 6l2.29 2.29l-4.88 4.88l-4-4L2 16.59L3.41 18l6-6l4 4l6.3-6.29L22 12V6h-6Z"></path>
          </svg>
        </div>
        <div class="num-sale">
          <h1>34.6k</h1>
          <h2>Sales</h2>
        </div>
      </div>
      <div class="sale-des">
        <div class="sales-icon icon">
          <svg style="width: 24px;height: 24px;margin: 10px 0px;">
            <path fill="currentColor"
                  d="M7 15h2c0 1.08 1.37 2 3 2s3-.92 3-2c0-1.1-1.04-1.5-3.24-2.03C9.64 12.44 7 11.78 7 9c0-1.79 1.47-3.31 3.5-3.82V3h3v2.18C15.53 5.69 17 7.21 17 9h-2c0-1.08-1.37-2-3-2s-3 .92-3 2c0 1.1 1.04 1.5 3.24 2.03C14.36 11.56 17 12.22 17 15c0 1.79-1.47 3.31-3.5 3.82V21h-3v-2.18C8.47 18.31 7 16.79 7 15Z"></path>
          </svg>
        </div>
        <div class="num-sale">
          <h1>$482k</h1>
          <h2>Total Profit</h2>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import VueApexCharts from "vue-apexcharts";

export default {
  name: "WeeklySalesStaticCard",
  components: {
    VueApexCharts
  },
  data() {
    return {
      chartOptions: {
        chart: {
          type: 'bar',
          height: 350,
          stacked: true,
          toolbar: {
            show: false,
          },
        },
        fill: {
          colors: ['#d987ff']
        },
        plotOptions: {
          bar: {
            borderRadius: 3,
            columnWidth: '41%',
            startingShape: 'rounded',
            endingShape: 'rounded',
          },
        },
        xaxis: {
          axisBorder: {
            show: false,
          },
          axisTicks: {
            show: false,
          },
          categories: ['S', 'M', 'T', 'W', 'T', 'F', 'S'],
          labels: {
            show: true,
          },
        },
        yaxis: {
          labels: {
            show: false,
          },
        },
        grid: {
          strokeDashArray: 10,
          padding: {
            left: -10,
            top: -10,
          },
        },
        dataLabels: {
          enabled: false,
        },
        legend: {
          show: false,
        },
        stroke: {
          curve: 'smooth',
          width: 0,
          colors: ['#c37dff'],
        },
        responsive: [
          {
            breakpoint: 1650,
            options: {
              plotOptions: {
                bar: {
                  borderRadius: 10,
                  columnWidth: '50%',
                },
              },
            },
          },
        ],
      },
      series: [{
        name: 'series-1',
        data: [30, 40, 35, 50, 49, 60, 23]
      }]
    }
  }
}
</script>

<style scoped>
html, body, div, span, h1, h2, h3, h4, h5, h6, p, a {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}


.containers {
  display: flex;
  width: 85%;
  margin: 0 auto;
  margin-top: 50px;
  flex-wrap: wrap;
  gap: 30px;
}

.w-sales {
  width: 30%;
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 0 15px #d0d0d0;
  padding: 10px 20px;
}

.tatal-sales {
  align-items: center;
  display: flex;
  justify-content: space-between;
}

.tatal-head h2 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 2rem;
}

.tatal-head h3 {
  font-size: .875rem;
  font-weight: 400;
}

.sale-graph {
  margin-top: 40px;
}

.sale-profit {
  align-items: center;
  margin: 22px 0px;
  display: flex;
  justify-content: space-between;
}

.sale-des {
  display: flex;
  margin: 10px 10px;
  align-items: center;
  gap: 20px;
}

.sales-icon {
  width: 44px;
  background-color: rgb(244, 245, 250);
  color: rgb(145, 85, 253);
  height: 44px;
  text-align: center;
  border-radius: 6px;
}

.sales-icon h2 {
  font-size: .875rem;
  font-weight: 400;
  padding: 20px;
}

.num-sale h1 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 2rem;
}
</style>
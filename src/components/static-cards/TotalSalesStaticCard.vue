<template>
  <q-card class="sale-analytics" style="width: 22.5%">
    <q-card-section class="tatal-sales" style="margin-top: 20px">
      <div class="tatal-head">
        <h2>Total Sales </h2>
        <h3>$21,845</h3>
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
  </q-card>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'

export default {
  name: "TotalSalesStaticCard",
  components: {
    // eslint-disable-next-line vue/no-unused-components
    VueApexCharts
  },
  data() {
    return {
      download_image: '@/assets/download.png',
      chartOptions: {
        chart: {
          id: 'vuechart-example',
          toolbar: {
            show: false,
          },
        },
        stroke: {
          curve: 'smooth',
          width: 3,
          lineCap: 'round',
          fill: 'gradient',
          colors: ['#fff'],
        },
        fill: {
          type: 'gradient',
          gradient: {
            shade: 'dark',
            gradientToColors: ['#2de100'],
            shadeIntensity: 1,
            type: 'horizontal',
            opacityFrom: 1,
            opacityTo: 1,
            stops: [0, 100, 100, 100]
          },
        },
        xaxis: {
          categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
          labels: {
            show: true,
          },
        },
        yaxis: {
          labels: {
            show: false
          }
        }
      },
      series: [{
        name: 'series-1',
        data: [30, 40, 35, 50, 49, 60]
      }]
    }
  },
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

.sale-analytics {
  width: 20%;
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
  font-size: 1.25rem;
  font-weight: 400;
}

.sale-graph {
  margin-top: 40px;
}

.actvty-item, .sale-profit {
  align-items: center;
  display: flex;
  justify-content: space-between;
}
</style>
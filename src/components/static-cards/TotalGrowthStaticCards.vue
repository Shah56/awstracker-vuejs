<template>
  <q-card class="t-growth" style="width: 16.5%">
    <q-card-section class="clmn">
      <h2>42.5k</h2>
      <div class="sale-graph">
        <vue-apex-charts
            :options="chartOptions"
            :series="series"
            height="140px"
        ></vue-apex-charts>
      </div>
      <div class="num-sale">
        <p>Total Growth</p>
      </div>
    </q-card-section>
    <q-card-section class="clmn">
      <div class="tatal-sales">
        <div class="tatal-head">
          <svg style="width: 24px;height: 24px;">
            <path fill="currentColor"
                  d="M20 7h-4V5l-2-2h-4L8 5v2H4c-1.1 0-2 .9-2 2v5c0 .75.4 1.38 1 1.73V19c0 1.11.89 2 2 2h14c1.11 0 2-.89 2-2v-3.28c.59-.35 1-.99 1-1.72V9c0-1.1-.9-2-2-2M10 5h4v2h-4V5M4 9h16v5h-5v-3H9v3H4V9m9 6h-2v-2h2v2m6 4H5v-3h4v1h6v-1h4v3Z"></path>
          </svg>
        </div>
        <div class="kabab-menu">
          <svg style="width: 24px;height: 24px;">
            <path fill="currentColor"
                  d="M12 16a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2Z"></path>
          </svg>
        </div>
      </div>
      <div class="clmn-content">
        <h3>New Project</h3>
        <h4>862<span>-18%</span></h4>
        <span class="year">Year 2021</span>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import VueApexCharts from "vue-apexcharts";

export default {
  name: "TotalGrowthStaticCards",
  components: {
    VueApexCharts
  },
  data() {
    return {
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
            show: false,
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

.t-growth {
  display: flex;
  width: 15%;
  flex-direction: column;
  gap: 15px;
}

.clmn {
  border-radius: 6px;
  padding: 20px;
  box-shadow: 0 0 15px #d0d0d0;
  background-color: white;
}

.clmn h2 {
  font-size: 1.25rem;
  font-weight: 500;
}

.num-sale p {
  font-size: 1rem;
  font-weight: 600;
}

.clmn .sale-graph {
  margin: 15px 0px;
  height: 160px;
}

.tatal-sales {
  align-items: center;
  display: flex;
  justify-content: space-between;
}

.tatal-head {
  color: white;
  background-color: rgb(145, 85, 253);
  border-radius: 50%;
  padding: 6px 8px;
}

.clmn h3 {
  font-size: .875rem;
  font-weight: 600;
  margin: 16px 0px;
}

.clmn h4 {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 12px;
}

.clmn h4 span {
  font-size: 0.75rem;
  font-weight: 400;
  margin-left: 10px;
  color: rgb(255, 76, 81);
}

.clmn span.year {
  font-size: .75rem;
}

.q-card {
  box-shadow: none;
}
</style>
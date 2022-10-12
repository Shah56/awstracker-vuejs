<template>
  <q-card class="Sales-Overview" style="width: 49%">
    <q-card-section class="tatal-sales">
      <div class="tatal-head">
        <h2>Sales Overview</h2>
      </div>
      <div class="kabab-menu">
        <svg style="width: 24px;height: 24px;">
          <path fill="currentColor"
                d="M12 16a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2m0-6a2 2 0 0 1 2 2a2 2 0 0 1-2 2a2 2 0 0 1-2-2a2 2 0 0 1 2-2Z"></path>
        </svg>
      </div>
    </q-card-section>
    <q-card-section class="sales-det">
      <q-card-section class="sale-grph">
        <vue-apex-charts
            :options="chartOptions"
            :series="series"
            height="250px"
        ></vue-apex-charts>
      </q-card-section>
      <q-card-section class="sales-des">
        <div class="sale-des">
          <div class="sales-icon icon">
            <svg style="width: 24px;height: 24px;margin: 10px 0px;">
              <path fill="currentColor"
                    d="M7 15h2c0 1.08 1.37 2 3 2s3-.92 3-2c0-1.1-1.04-1.5-3.24-2.03C9.64 12.44 7 11.78 7 9c0-1.79 1.47-3.31 3.5-3.82V3h3v2.18C15.53 5.69 17 7.21 17 9h-2c0-1.08-1.37-2-3-2s-3 .92-3 2c0 1.1 1.04 1.5 3.24 2.03C14.36 11.56 17 12.22 17 15c0 1.79-1.47 3.31-3.5 3.82V21h-3v-2.18C8.47 18.31 7 16.79 7 15Z"></path>
            </svg>
          </div>
          <div class="num-sale">
            <h2>Number of Sales</h2>
            <h1>$86,400</h1>
          </div>
        </div>
        <hr>
        <div class="sale-info">
          <div class="p-info">
            <p>
              <svg style="font-size:12px;width: 12px;height: 12px;">
                <path fill="currentColor"
                      d="M12 2A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10A10 10 0 0 0 12 2Z"></path>
              </svg>
              <span>Apparel</span>
            </p>
            <p>$1,840</p>
          </div>
          <div class="p-info">
            <p>
              <svg style="font-size:12px;width: 12px;height: 12px;">
                <path fill="currentColor"
                      d="M12 2A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10A10 10 0 0 0 12 2Z"></path>
              </svg>
              <span>Apparel</span>
            </p>
            <p>$1,840</p>
          </div>
          <div class="p-info">
            <p>
              <svg style="font-size:12px;width: 12px;height: 12px;">
                <path fill="currentColor"
                      d="M12 2A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10A10 10 0 0 0 12 2Z"></path>
              </svg>
              <span>Apparel</span>
            </p>
            <p>$1,840</p>
          </div>
          <div class="p-info">
            <p>
              <svg style="font-size:12px;width: 12px;height: 12px;">
                <path fill="currentColor"
                      d="M12 2A10 10 0 0 0 2 12a10 10 0 0 0 10 10a10 10 0 0 0 10-10A10 10 0 0 0 12 2Z"></path>
              </svg>
              <span>Apparel</span>
            </p>
            <p>$1,840</p>
          </div>
        </div>
      </q-card-section>
    </q-card-section>
  </q-card>
</template>

<script>
import VueApexCharts from 'vue-apexcharts'

export default {
  name: "SalesOverviewStaticCard",
  components: {
    VueApexCharts
  },
  data() {
    return {
      chartOptions: {
        chart: {
          type: 'donut',
          height: 350,
          stacked: true,
          toolbar: {
            show: false,
          },
        },
        plotOptions: {
          bar: {
            borderRadius: 10,
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
          labels: {
            show: false,
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
          width: 6,
          lineCap: 'round',
          colors: ['#fff'],
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
      series: [30, 40, 35, 50]
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

.Sales-Overview {
  width: 42%;
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
  font-size: 1.5rem;
  font-weight: 600;
  line-height: 1.5rem;
}

.sales-det, .sale-des {
  display: flex;
  align-items: center;
  gap: 20px;
  margin: 30px 0px;
}

.sale-des {
  margin: 10px 10px;
}

.sales-icon {
  width: 44px;
  color: rgb(145, 85, 253);
  background-color: rgb(244, 245, 250);
  height: 44px;
  text-align: center;
  border-radius: 6px;
}

.sales-icon h2 {
  font-size: .875rem;
  font-weight: 400;
  letter-spacing: .0094rem;
  padding: 20px;
}

.num-sale h1 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 2rem;
}

.sale-info {
  display: flex;
  flex-wrap: wrap;
}

.p-info {
  height: 75px;
  width: 50%;
}

.p-info p {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 2rem;
  letter-spacing: .0094rem;
}

.p-info p svg {
  color: rgb(145, 85, 253);
}

.p-info p span {
  font-size: .875rem;
  margin-left: 5px;
  font-weight: 400;
  letter-spacing: .0094rem;
}
</style>
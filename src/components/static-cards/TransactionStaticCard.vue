<template>
  <q-card class="Transactions" style="width: 49%">
    <q-card-section class="text">
      <h3>Transactions</h3>
    </q-card-section>
    <h6><span>Total 48.5% growth :sunglasses:</span> this month</h6>
    <q-card-section class="analytics">
      <div class="sales">
        <div class="sales-icon">
          <svg style="width: 24px;height: 24px;margin: 10px 0px;">
            <path fill="currentColor"
                  d="m16 6l2.29 2.29l-4.88 4.88l-4-4L2 16.59L3.41 18l6-6l4 4l6.3-6.29L22 12V6h-6Z"></path>
          </svg>
        </div>
        <q-item-label class="caption">
          <h6>Sales</h6>
          <span>245k</span>
        </q-item-label>
      </div>
      <div class="sales">
        <div class="sales-icon-green">
          <svg style="width: 24px;height: 24px;margin: 10px 0px;">
            <path fill="currentColor"
                  d="M12 4a4 4 0 0 1 4 4a4 4 0 0 1-4 4a4 4 0 0 1-4-4a4 4 0 0 1 4-4m0 2a2 2 0 0 0-2 2a2 2 0 0 0 2 2a2 2 0 0 0 2-2a2 2 0 0 0-2-2m0 7c2.67 0 8 1.33 8 4v3H4v-3c0-2.67 5.33-4 8-4m0 1.9c-2.97 0-6.1 1.46-6.1 2.1v1.1h12.2V17c0-.64-3.13-2.1-6.1-2.1Z"></path>
          </svg>
        </div>
        <div class="caption">
          <h6>Customers</h6>
          <span>245k</span>
        </div>
      </div>
      <div class="sales">
        <div class="sales-icon-yellow">
          <svg style="width: 24px;height: 24px;margin: 10px 0px;">
            <path fill="currentColor"
                  d="M22 17h-4v-7h4m1-2h-6a1 1 0 0 0-1 1v10a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V9a1 1 0 0 0-1-1M4 6h18V4H4a2 2 0 0 0-2 2v11H0v3h14v-3H4V6Z"></path>
          </svg>
        </div>
        <div class="caption">
          <h6>Product</h6>
          <span>245k</span>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: "TransactionStaticCard"
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

body {
  background-color: #F4F5FA;
}

.containers {
  display: flex;
  width: 85%;
  margin: 0 auto;
  margin-top: 50px;
  flex-wrap: wrap;
  gap: 30px;
}
.Transactions {
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 0 15px #d0d0d0;
  width: 45%;
  padding: 10px 20px;
}

.analytics {
  display: flex;
  margin: 21px 0px;
  gap: 70px;
}

.text {
  font-size: 1.5rem;
  margin: 20px 0px;
  font-weight: 500;
}

.Transactions h6 {
  font-size: 1rem;
}

.Transactions h6 span {
  font-weight: 600;
}

.sales {
  gap: 15px;
  display: flex;
}

.sales-icon {
  width: 44px;
  background-color: rgb(145, 85, 253);
  height: 44px;
  text-align: center;
  color: white;
  border-radius: 6px;
}
.sales-icon-green {
  width: 44px;
  background-color: #2de100;
  height: 44px;
  text-align: center;
  color: white;
  border-radius: 6px;
}
.sales-icon-yellow {
  width: 44px;
  background-color: #f3bc07;
  height: 44px;
  text-align: center;
  color: white;
  border-radius: 6px;
}

.caption {
  display: flex;
  flex-direction: column;
}

.caption span {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: 26px;
}

.caption .h6 {
  font-size: 1.25rem;
  font-weight: 500;
  padding: 0.5rem 1rem;
}
.sale-analytics, .Sales-Overview, .ActivityTimeline, .meetup {
  width: 20%;
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 0 15px #d0d0d0;
  padding: 10px 20px;
}

.tatal-sales, .actvty-item, .sale-profit {
  align-items: center;
  display: flex;
  justify-content: space-between;
}

</style>
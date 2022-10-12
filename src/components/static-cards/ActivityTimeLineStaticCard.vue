<template>
  <q-card class="ActivityTimeline" style="width:47.5%">
    <h2>Activity Timeline</h2>
    <q-card-section class="actvty-item">
      <div class="left">
        <h3>8 Invoices have been paid</h3>
        <p>Invoices have been paid to the company.</p>
        <div class="profile">
          <svg style="width: 24px;height: 24px;">
            <path fill="currentColor"
                  d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2m-9.5 8.5c0 .8-.7 1.5-1.5 1.5H7v2H5.5V9H8c.8 0 1.5.7 1.5 1.5v1m5 2c0 .8-.7 1.5-1.5 1.5h-2.5V9H13c.8 0 1.5.7 1.5 1.5v3m4-3H17v1h1.5V13H17v2h-1.5V9h3v1.5m-6.5 0h1v3h-1v-3m-5 0h1v1H7v-1Z"></path>
          </svg>
          <h4>invoice.pdf</h4>
        </div>
      </div>
      <div class="day-date">
        <p>Wednesday</p>
      </div>
    </q-card-section>
    <q-card-section class="actvty-item">
      <div class="left">
        <h3>Create a new project for client :sunglasses:</h3>
        <p>Invoices have been paid to the company.</p>
        <div class="profile">
          <img src="../../assets/profile.png" style="width: 24px;height:24px;" alt="" srcset="">
          <h4>John Doe (Client)</h4>
        </div>
      </div>
      <div class="day-date">
        <p>April, 18</p>
      </div>
    </q-card-section>
    <q-card-section class="actvty-item">
      <div class="left">
        <h3>Order #37745 from September</h3>
        <p>Invoices have been paid to the company.</p>
      </div>
      <div class="day-date">
        <p>Wednesday</p>
      </div>
    </q-card-section>
    <q-card-section class="actvty-item">
      <div class="left">
        <h3>Public Meeting</h3>
      </div>
      <div class="day-date">
        <p>September, 30</p>
      </div>
    </q-card-section>
    <q-card-section class="actvty-item">
      <div class="left">
        <h3>Create a new project for client :sunglasses:</h3>
        <p>Invoices have been paid to the company.</p>
        <div class="profile">
          <img src="../../assets/profile.png" style="width: 24px;height:24px;" alt="" srcset="">
          <h4>John Doe (Client)</h4>
        </div>
      </div>
      <div class="day-date">
        <p>April, 18</p>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: "ActivityTimeLineStaticCard"
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

.ActivityTimeline {
  width: 42%;
  border-radius: 6px;
  background-color: white;
  box-shadow: 0 0 15px #d0d0d0;
  padding: 10px 20px;
}

.ActivityTimeline h2 {
  font-size: 1.25rem;
  font-weight: 500;
  padding: 15px 0px;
  line-height: 1.5rem;
}

.actvty-item {
  display: flex;
  margin: 20px 0px;
  justify-content: space-between;
}

.actvty-item h3 {
  font-weight: 600;
  font-size: 1rem;
  line-height: 1.5rem;
}

.profile {
  display: flex;
  margin-top: 10px;
  gap: 2px;
  align-items: center;
}

.profile svg {
  color: rgb(255, 76, 81);
}

.day-date p {
  font-size: .75rem;
  line-height: 1rem;
}
</style>
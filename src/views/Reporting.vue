<template>
  <div class="containers">
    <static-card-with-images
        :avatar="trainingOptions.avatar"
        :avatar-width="trainingOptions.avatarWidth"
        :change="trainingOptions.change"
        :chip-color="trainingOptions.chipColor"
        :chip-text="trainingOptions.chipText"
        :statistics="trainingOptions.statistics"
        :stat-title="trainingOptions.statTitle"
    ></static-card-with-images>
    <static-card-with-images
        :avatar="sessionOptions.avatar"
        :avatar-width="sessionOptions.avatarWidth"
        :change="sessionOptions.change"
        :chip-color="sessionOptions.chipColor"
        :chip-text="sessionOptions.chipText"
        :statistics="sessionOptions.statistics"
        :stat-title="sessionOptions.statTitle"
    ></static-card-with-images>
    <transaction-static-card></transaction-static-card>
    <total-sales-static-card></total-sales-static-card>
    <revenue-report-static-card></revenue-report-static-card>
    <sales-overview-static-card></sales-overview-static-card>
    <activity-time-line-static-card></activity-time-line-static-card>
    <weekly-sales-static-card></weekly-sales-static-card>
    <total-growth-static-cards></total-growth-static-cards>
    <upgrade-plan-static-card></upgrade-plan-static-card>
    <meeting-schedule-static-card></meeting-schedule-static-card>
    <developer-meetup-static-card></developer-meetup-static-card>


  </div>
</template>

<script>
import StaticCardWithImages from "@/components/static-cards/StaticCardWithImages";
import TransactionStaticCard from "@/components/static-cards/TransactionStaticCard";
import TotalSalesStaticCard from "@/components/static-cards/TotalSalesStaticCard";
import RevenueReportStaticCard from "@/components/static-cards/RevenueReportStaticCard";
import SalesOverviewStaticCard from "@/components/static-cards/SalesOverviewStaticCard";
import ActivityTimeLineStaticCard from "@/components/static-cards/ActivityTimeLineStaticCard";
import WeeklySalesStaticCard from "@/components/static-cards/WeeklySalesStaticCard";
import TotalGrowthStaticCards from "@/components/static-cards/TotalGrowthStaticCards";
import UpgradePlanStaticCard from "@/components/static-cards/UpgradePlanStaticCard";
import MeetingScheduleStaticCard from "@/components/static-cards/MeetingScheduleStaticCard";
import DeveloperMeetupStaticCard from "@/components/static-cards/DeveloperMeetupStaticCard";

export default {
  name: "Reporting",
  components: {
    StaticCardWithImages,
    TransactionStaticCard,
    TotalSalesStaticCard,
    RevenueReportStaticCard,
    SalesOverviewStaticCard,
    ActivityTimeLineStaticCard,
    WeeklySalesStaticCard,
    TotalGrowthStaticCards,
    UpgradePlanStaticCard,
    MeetingScheduleStaticCard,
    DeveloperMeetupStaticCard
  },
  setup() {
    const trainingOptions = {
      statTitle: 'Trainings',
      statistics: '15',
      change: '+38%',
      chipText: 'Month of June',
      chipColor: 'primary',
      avatar: require('../assets/9.png'),
      avatarWidth: '110px',
    }
    const sessionOptions = {
      statTitle: 'Sessions',
      statistics: '32',
      change: '+25%',
      chipText: 'Month of June',
      chipColor: 'primary',
      avatar: require('../assets/10.png'),
      avatarWidth: '110px',
    }
    return {
      trainingOptions,
      sessionOptions,
    }
  },
}
</script>

<style scoped>
html, body, div, span,h1, h2, h3, h4, h5, h6, p,a {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
}
body{
    background-color: #F4F5FA;
}
.containers{
    display: flex;
    width: 85%;
    margin: 0 auto;
    margin-top: 50px;
    flex-wrap: wrap;
    gap: 30px;
    margin-bottom: 50px;
 }
 .rating{
    position: relative;
    width: 22%;
    border-radius: 6px;
    background-color: white;
    box-shadow: 0 0 15px #d0d0d0;
    display: flex;
}
.l-content{
    padding: 25px 20px;
}
.l-content h3{
    font-size: 2rem;
    line-height: 1.5rem;
    font-weight: 500;
    margin-bottom: 16px;
}
.l-content h4 {
    font-weight: 500;
    line-height: 2rem;
    margin-bottom: 12px;
}
.l-content h4 span {
    font-size: 0.75rem;
    font-weight: 400;
    margin-left: 10px;
    color: rgb(86,202,0);
}
.l-content span.year {
    height: 26px;
    background-color: rgba(145,85,253,0.2);
    color: rgb(145,85,253);
    font-size: .75rem;
    border-radius: 10px;
    padding: 5px 10px;
}
.rat-img {
    position: absolute;
    right: 0;
    top: -22px;
}
.Transactions{
    border-radius: 6px;
    background-color: white;
    box-shadow: 0 0 15px #d0d0d0;
    width: 45%;
    padding: 10px 20px;
}
.analytics{
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
.sales{
    gap: 15px;
    display: flex;
}
.sales-icon {
    width: 44px;
    background-color: rgb(145,85,253);
    height: 44px;
    text-align: center;
    color: white;
    border-radius: 6px;
}
.caption{
    display: flex;
    flex-direction: column;
}
.caption span {
    font-size: 1.25rem;
    font-weight: 600;
    line-height: 26px;
}
.caption .h6{
    font-size: 1.25rem;
    font-weight: 500;
    padding: 0.5rem 1rem;
}
.t-sales{
    display: flex;
    justify-self: space-between;
}
.sale-analytics,.Sales-Overview,.ActivityTimeline,.meetup{
    width: 20%;
    border-radius: 6px;
    background-color: white;
    box-shadow: 0 0 15px #d0d0d0;
    padding: 10px 20px;
}
.tatal-sales,.actvty-item,.sale-profit{
    align-items: center;
    display: flex;
    justify-content: space-between;
}
.sale-graph{
    margin-top: 40px;
}
.Sales-Overview,.ActivityTimeline{
    width: 42%;
}
.sales-det,.sale-des{
    display: flex;
    align-items: center;
    gap: 20px;
}
.actvty-item {
    margin:20px 0px;
}
.profile{
    display: flex;
    margin-top: 10px;
    gap: 2px;
    align-items: center;
}
.profile svg{
    color: rgb(255,76,81);
}
.dot {
    height: 15px;
    width: 15px;
    background-color: red;
    border-radius: 50%;
  }
  .w-sales{
    width: 30%;
  }
  .your-attention,.shedule{
    display: flex;
    gap: 10px;
  }
.tatal-head h2{
    font-size: 1.5rem;
    font-weight: 600;
    line-height: 1.5rem;
}
.tatal-head h3{
    font-size: 1.5rem;
    font-weight: 400;
    line-height: 1.5rem;
    letter-spacing: .0094rem;
}
.icon{
    background-color:rgb(244, 245, 250) ;
    color: rgb(145,85,253);
}
.icon h2{
    font-size: .875rem;
    font-weight: 400;
    letter-spacing: .0094rem;
    padding: 20px;
}
.num-sale h1,.p-info p{
    font-size: 1.25rem;
    font-weight: 600;
    line-height: 2rem;
    letter-spacing: .0094rem;
}
.sale-info{
    display: flex;
    flex-wrap: wrap;
}
.p-info{
    height: 75px;
    width: 50%;
}
.p-info p span{
    font-size: .875rem;
    margin-left: 5px;
    font-weight: 400;
    letter-spacing: .0094rem;
}
.p-info p svg{
    color: rgb(145,85,253);
}
/* Activity Timeline  */
.ActivityTimeline h2{
    font-size: 1.25rem;
    font-weight: 500;
    padding: 15px 0px;
    line-height: 1.5rem;
}
.actvty-item h3{
    font-weight: 600!important;
    font-size: 1rem;
    line-height: 1.5rem;
}
.day-date p{
    font-size: .75rem;
    line-height: 1rem;
}
.analytic-clmn{
    display: flex;
    flex-direction: column;
}
.t-growth {
    display: flex;
    /* background-color: white; */
    width: 15%;
    flex-direction: column;
    gap: 15px;
}
.clmn{
    border-radius: 6px;
    padding: 20px;
    background-color: white;
}
.clmn h3{
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
    color: rgb(255,76,81);
}
.clmn span.year {
    font-size: .75rem;
}
.clmn .sale-graph {
    margin: 15px 0px;
}
.t-growth .clmn .tatal-head{
    color: white;
    background-color: rgb(145,85,253);
    border-radius: 50%;
    padding: 6px 8px;
}
/* Upgrade Your Plan  */
.upgrade-plan{
    width: 29%;
}
.upgrade-plan .tatal-head{
    margin: 10px 0px;
}
.upgrade-plan .tatal-sales h2{
    font-size: 1.25rem;
    font-weight: 600;
}
.upgrade-plan p{
    font-size: 1rem;
    margin: 10px 0px;
}
.upgrade-plan .sale-profit{
    background-color:rgb(244, 245, 250);
    padding: 10px 10px;
    border-radius: 6px;
    margin: 15px 0px;
}
.upgrade-plan .sales-img{
    border: 1px solid rgb(145,85,253);
    padding: 10px 10px;
    border-radius: 5px;
}
.upgrade-plan .num-sale h2{
    color: rgb(145,85,253);
}
.upgrade-plan .p-sale span{
    font-size: 1.75rem;
    font-weight: 600;
}
.upgrade-plan .p-sale sup {
    font-size: .9rem;
    line-height: 1rem;
    font-weight: 400;
}
.paymnt-detail h2{
    font-weight: 600;
    margin-left: 10px;
}
.paymnt-detail .sale-profit{
    background-color: white;
    align-items: center;
    padding: 0px 0px;
}
.upgrade-plan .num-sale p{
    margin: 0;
    color: gray;
}
.cvv-nmb input{
    height: 40px;
    border-style: none;
    width: 80px;
    text-align: center;
    border-radius: 6px;
    color: grey;
    border: 1px solid grey;
}
.paymnt-method a{
    font-size: 1rem;
    text-decoration: none;
    color: rgb(145,85,253);
}
.paymnt-method .input-field input{
    width: 100%;
    height: 40px;
    margin: 10px 0px;
    border-style: none;
    text-align: center;
    border-radius: 6px;
    color: grey;
    border: 1px solid grey;
}
.paymnt-method button{
    width: 100%;
    height: 40px;
    margin: 10px 0px;
    border-style: none;
    text-align: center;
    border-radius: 6px;
    color: white;
    background-color: rgb(145,85,253);
}
/* Meeting Shedule */
.meeting-shdl{
    width: 29%;
}
.meeting-shdl .profile img {
    border-radius: 50%;
}
.meeting-shdl .num-sale h2{
    font-weight: 600;
    font-size: 1rem;
    line-height: 2rem;
}
span{
    color: grey;
}
.p-sale span{
    background-color: rgba(145,85,253,0.2);
    color: rgb(145,85,253);
    font-size: .75rem;
    border-radius: 15px;
    padding: 8px 10px;
}
.actvty-item, .sale-profit {
    margin: 22px 0px;
}
/*  Developer Meetup */
.meetup{
    padding: 0px 0px;
    width: 29%;
}
.dev-meet{
    padding: 10px 20px;
}
.dev-meet .num-sale h2{
    font-size: 1rem;
    line-height: 1.5rem;
    font-weight: 600;
    margin-bottom: 4px;
}
.dev-meet .sale-des{
    margin: 10px 10px;
}
.dev-meet .sales-icon p{
    font-weight: 600;
    margin-top: 5px;
    font-size: 1.5rem;
}
.dev-meet .sales-icon {
    height: auto;
    padding: 5px 0px;
    width: 120px;
    color: rgb(145,85,253);
    background-color:rgb(244, 245, 250);
}
.dev-meet .num-sale p{
    font-size: .75rem;
    line-height: 1rem;
}
.dev-meet .your-attention{
    gap: 40px;
    margin: 20px 0px;
}
.dev-meet .interested {
    text-align: center;
}
.dev-meet .shedule {
    margin: 10px 0px;
}
</style>
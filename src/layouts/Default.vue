<template>
  <div>
    <q-toolbar class="bg-primary text-white toolbarSpace" style="background-color: #fff !important; height: 60px;">

      <!--      <q-btn flat @click="drawers()" round dense icon="menu"/>-->

      <!--      <q-separator dark vertical inset/>-->

      <!--      <q-btn flat label="Stealth Connect" @click="mainPage()"/>-->
      <!--      <q-btn icon="local_fire_department"-->
      <!--             class="q-mr-sm"-->
      <!--             color="orange"-->
      <!--             flat round dense-->
      <!--             @click="launchFleet"-->
      <!--             size="xs"-->
      <!--      >-->
      <!--&lt;!&ndash;        <q-tooltip&ndash;&gt;-->
      <!--&lt;!&ndash;            content-class="bg-grey"&ndash;&gt;-->
      <!--&lt;!&ndash;            content-style="font-size: 16px"&ndash;&gt;-->
      <!--&lt;!&ndash;            :offset="[10, 10]"&ndash;&gt;-->
      <!--&lt;!&ndash;        >&ndash;&gt;-->
      <!--&lt;!&ndash;          Enable Drones&ndash;&gt;-->
      <!--&lt;!&ndash;        </q-tooltip>&ndash;&gt;-->
      <!--      </q-btn>-->

      <!--      <q-separator dark vertical/>-->
      <!--      <div v-for="item of menuItems" :key="item.label">-->
      <!--        <q-btn stretch flat-->
      <!--               :icon="item.icon"-->
      <!--               :label="item.label"-->
      <!--               :to="item.page"-->
      <!--        />-->
      <!--      </div>-->

      <q-space/>

      <!--
        notice shrink property since we are placing it
        as child of QToolbar
      -->

      <q-separator/>

      <q-btn-dropdown
          flat style="float: left; background-color: #171717 !important; color: white">
        <template v-slot:label>
          <div class="row items-center no-wrap">
            <q-icon left name="person"/>
            <div class="text-center">
              {{ fullName }}
            </div>
          </div>
        </template>
        <q-list>

          <q-item style="background-color: grey !important; color: #fff">
            <q-item-section avatar>
              <q-icon left name="account_circle" style="font-size: 45px"/>
            </q-item-section>
            <q-item-section>
              <q-item-label style="font-weight: 600">{{fullName}}</q-item-label>
              <q-item-label>{{userEmail}}</q-item-label>
            </q-item-section>
          </q-item>

          <q-separator></q-separator>

          <q-item clickable v-close-popup style="background-color: grey !important; color: #fff">
            <q-item-section avatar>
              <q-icon left name="person"/>
            </q-item-section>
            <q-item-section @click="profileClick()">
              <q-item-label>Profile</q-item-label>
            </q-item-section>
          </q-item>

          <q-separator></q-separator>

          <q-item clickable v-close-popup style="background-color: grey !important; color: #fff">
            <q-item-section avatar>
              <q-icon left name="settings"/>
            </q-item-section>
            <q-item-section>
              <q-item-label>Settings</q-item-label>
            </q-item-section>
          </q-item>

          <q-separator></q-separator>

          <q-item clickable v-close-popup @click="signOut()" style="background-color: grey !important; color: #fff">
            <q-item-section>
              <q-icon left name="exit_to_app" style="font-size: 30px"/>
            </q-item-section>
            <q-item-section>
              <q-item-label style="margin-left: -65px">Logout</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-btn-dropdown>
    </q-toolbar>
    <!--  For Side Bar -->
    <div class="forSideBar" id="forSideBar">
      <q-layout view="lHh Lpr lff" container style="height: 896px; border-color: #171717 !important; margin-top: -55px"
                class=" rounded-borders">
        <q-header elevated class="bg-black" style="border-color: #171717 !important;">
          <q-drawer
              v-model="drawer"
              show-if-above
              :width="250"
              :breakpoint="55"
              :mini="miniState"
              @mouseover="mouseOver()"
              @mouseout="mouseOut()"
              content-class="bg-grey-3" class="sideBarDrawer"
          >
            <q-scroll-area class="fit" style="background-color: #171717 !important; border-color: #171717 !important;">

              <q-list padding>

                <template>
                  <q-item v-ripple style="height: 60px; cursor:pointer;">
                    <q-item-section avatar>
                      <img src="../assets/TS.png" alt="" style="width: 35px; height: 35px;"/>
                    </q-item-section>
                    <q-item-section style="font-size: 16px; color: #fff;">
                      Stealth Connect
                    </q-item-section>
                  </q-item>
                </template>

                <template v-for="(menuItem, index) in menuList">
                  <q-list :key="index">
                    <q-expansion-item v-if="menuItem.children" clickable v-ripple :label="menuItem.label"
                                      :icon="menuItem.icon"
                                      :id="menuItem.label"
                                      expand-separator
                                      @click="expandClick(menuItem)" :active="menuItem.check === true"
                                      active-class="activeClass"
                                      style="height: 50px; margin-bottom:10px; margin-top:10px; margin-left:5px;">

                      <template v-for="(child, indexChild) in menuItem.children">
                        <q-item :key="indexChild" clickable v-ripple :label="child.label" active-class="activeClass"
                                style="padding-left: 50px;">
                          <q-item-section avatar>
                            <q-icon :name="child.icon"
                                    style="font-size: 18px; color: white !important;"></q-icon>
                          </q-item-section>
                          <q-item-section
                              style="font-size: 14px; color: #fff;">
                            {{ child.label }}
                          </q-item-section>
                        </q-item>
                      </template>

                    </q-expansion-item>


                    <q-item :key="index" v-else clickable v-ripple :label="menuItem.label"
                            :icon="menuItem.icon"
                            @click="itemClicked(menuItem)" :active="menuItem.check === true"
                            active-class="activeClass"
                            style="height: 50px; margin-bottom:10px; margin-top:10px; margin-left:5px;">
                      <q-item-section avatar>
                        <q-icon :name="menuItem.icon"
                                style="font-size: 18px; color: white !important;"></q-icon>
                      </q-item-section>
                      <q-item-section
                          style="font-size: 14px; color: #fff;">
                        {{ menuItem.label }}
                      </q-item-section>
                    </q-item>
                  </q-list>

                  <q-separator :key="'sep' + index" v-if="menuItem.separator"></q-separator>
                </template>

              </q-list>
            </q-scroll-area>
          </q-drawer>
        </q-header>
      </q-layout>

    </div>
    <div class="forContent z-max" id="forContent">
      <q-layout view="lHh Lpr lff" container style="width: 100%;height: 850px; border-color: #181414 !important;"
                class="shadow-2 rounded-borders">
        <q-page-container>

          <router-view/>
        </q-page-container>
      </q-layout>

    </div>

  </div>
</template>

<script>
import {mapGetters, mapState} from "vuex";
import {Auth} from "aws-amplify";
import {ref} from 'vue'
import logo2 from '../assets/logo2.png'

export default {
  name: "default-layout",
  components: {
    // eslint-disable-next-line vue/no-unused-components
    logo2,
  },

  data() {
    return {
      photo: "",
      checkState: true,
      menuList: [
        {
          icon: 'dashboard',
          label: 'Dashboard',
          separator: false,
          check: true,
        },
        {
          icon: 'directions_car',
          label: 'Vehicles',
          separator: false,
          check: false,
          children: [
            {
              icon: 'my_location',
              label: 'Tracking',
              separator: false,
              check: false,
            },
            {
              icon: 'map',
              label: 'Geo Fencing',
              separator: false,
              check: false,
            },
            {
              icon: 'warning',
              label: 'Alerts',
              separator: false,
              check: false,
            },
            {
              icon: 'battery_charging_full',
              label: 'Battery Status',
              separator: false,
              check: false,
            },
          ]
        },
        {
          icon: 'construction',
          label: 'Equipment',
          separator: false,
          check: false,
          children: [
            {
              icon: 'my_location',
              label: 'Tracking',
              separator: false,
              check: false,
            },
            {
              icon: 'map',
              label: 'Geo Fencing',
              separator: false,
              check: false,
            },
            {
              icon: 'warning',
              label: 'Alerts',
              separator: false,
              check: false,
            },
            {
              icon: 'battery_charging_full',
              label: 'Battery Status',
              separator: false,
              check: false,
            },
          ]
        },
        {
          icon: 'gps_fixed',
          label: 'Drone Tracking',
          separator: false,
          check: false,
        },
        {
          icon: 'report',
          label: 'Reporting',
          separator: false,
          check: false,
        },
        {
          icon: 'integration_instructions',
          label: 'Integrations',
          separator: false,
          check: false,
        },
        {
          icon: 'help',
          label: 'Help',
          separator: false,
          check: false,
        },

      ],
      drawer: false,
      menuItems: [
        {
          icon: "house",
          page: "/",
          label: "Home"
        },
        {
          icon: "person_add",
          page: "agent",
          label: "Drone"
        },
        {
          icon: "local_shipping",
          page: "delivery",
          label: "Track"
        }
      ],
    };
  },
  setup() {
    return {
      drawerLeft: ref(false),
      drawerRight: ref(false),
      miniState: ref(false),
      link: ref('home')
    }
  },
  mounted() {
    document.getElementById('toggler').checked = true
  },
  methods: {
    mainPage() {
      this.$router.push('/')
    },
    mouseOver() {
      // const fc = document.getElementById('forContent')
      // fc.style.paddingLeft = '301px'
      // if (this.miniState === false && this.checkState === true) {
      //   this.miniState = false
      // } else if (this.miniState === true && this.checkState === false) {
      //   this.miniState = false
      // }
    },
    mouseOut() {
      // const fc = document.getElementById('forContent')
      // const sb = document.getElementById('forSideBar')
      // if (this.checkState === true) {
      //   this.miniState = false
      //   fc.style.paddingLeft = '301px'
      //   sb.style.width = '17.7%'
      // } else if (this.checkState === false && this.miniState === false) {
      //   this.miniState = true
      //   fc.style.paddingLeft = '55px'
      //   sb.style.width = '17.7%'
      // } else {
      //   fc.style.paddingLeft = '55px'
      //   sb.style.width = '3.7%'
      // }
    },

    expandClick(itemExpand) {
      if (itemExpand.label === 'Vehicles') {
        let expand = document.getElementById('Vehicles')
        if (expand.style.marginBottom === '200px') {
          expand.style.marginBottom = '0px'
        } else {
          expand.style.marginBottom = '200px'
        }
      } else if (itemExpand.label === 'Equipment') {
        let expand = document.getElementById('Equipment')
        if (expand.style.marginBottom === '200px') {
          expand.style.marginBottom = '0px'
        } else {
          expand.style.marginBottom = '200px'
        }
      }

    },

    stateDrawerManage() {
      var elm = document.getElementById('toggler');
      // elm.checked = !elm.checked;
      if (elm.checked === true) {
        this.miniState = false
        this.checkState = true
      } else {
        this.miniState = true
        this.checkState = false
      }
    },
    itemClicked(val) {
      if (val.label === 'Home') {
        this.$router.push('/')
      } else if (val.label === 'Drone') {
        this.launchFleet()
      } else if (val.label === 'Track') {
        console.log('Track')
      }
      let arr = [...this.menuList]
      arr.map((item) => {
        if (item.label === val.label) {
          item.check = true
        } else {
          item.check = false
        }
      })
      this.menuList = arr

    },
    drawers() {
      this.drawer = !this.drawer
    },
    profileClick() {
      this.$router.push('/profile')
    },
    async signOut() {
      try {
        await Auth.signOut();
        this.$router.push("/auth");
      } catch (error) {
        console.log("error signing out: ", error);
      }
    },
    async launchFleet() {

      let url = process.env.VUE_APP_APIURL

      const currentSession = await Auth.currentSession();
      this.jwt = currentSession.getIdToken().getJwtToken();
      const options = {
        headers: {
          'authorization': this.jwt
        }
      };

      let results = await this.$http.post(url + "launch_fleet", {}, options);

      if (results.status === 200) {
        this.$q.notify({
          color: "orange",
          position: "top",
          timeout: 5000,
          icon: "local_fire_department",
          message: results.data.msg,
        })
      } else {
        this.$q.notify({
          color: "orange",
          position: "top",
          timeout: 5000,
          icon: "warning",
          message: results.data.msg,
        })
      }

    },
  },
  computed: {
    ...mapState({
      user: (state) => state.profile.user,
    }),
    ...mapGetters({
      isAuthenticated: "profile/isAuthenticated",
      firstName: "profile/firstName",
      lastName: "profile/lastName",
      email: "profile/email",
    }),
    fullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    userEmail(){
      return `${this.email}`;
    }
  },
};
</script>

<style scoped>
.toolbar {
  min-height: 60px;
}

/*div#forSideBar .activeClass[data-v-c6c5ef5c] {*/
/*  background: linear-gradient(98deg, #c48eff, #9155fd 94%);*/
/*  color: black;*/
/*  border-bottom-right-radius: 29px;*/
/*  border-top-right-radius: 29px;*/
/*  transform: translate(-15px, 5px);*/
/*  padding-left: 32px;*/

/*}*/

div#forSideBar .q-item.q-item-type.row.no-wrap.q-item--clickable.q-link {
  margin-left: -10px;
}

#profile {
  height: 130px;
  background-color: #808080;
}

#menu-collapse {
  margin-top: 5%;
}

.right-itens a,
.right-itens button {
  margin-right: 10px;
}

.fixed-bottom {
  margin-bottom: 1%;
}

.activeClass {
  background: linear-gradient(98deg, #c48eff, #9155fd 94%);
  color: black;
  border-bottom-right-radius: 29px;
  border-top-right-radius: 29px;
  transform: translate(-15px, 5px);
  padding-left: 32px;
}

.fixed-bottom a img {
  width: 25px;
  height: 25px;
}

aside.q-drawer.q-drawer--left.q-drawer--standard.fixed.q-drawer--top-padding {
  width: 226px !important;
}

#menu-collapse {
  margin-top: 5%;
}

.layout-padding {
  padding: 1em 4em;
}

@media screen and (max-width: 600px) {
  .layout-padding {
    padding: 1.5em 0.5em;
  }
}

.menu-enter-active,
.scale-enter {
  -webkit-animation: moveFromLeftFade 0.9s ease both;
  animation: moveFromLeftFade 0.9s ease both;
}

.menu-leave-to,
.scale-leave-active {
  -webkit-animation: moveToLeft 0.9s ease both;
  animation: moveToLeft 0.9s ease both;
}

@-webkit-keyframes moveFromLeftFade {
  from {
    opacity: 0.3;
    -webkit-transform: translateX(-100%);
  }
}

@keyframes moveFromLeftFade {
  from {
    opacity: 0.3;
    -webkit-transform: translateX(-100%);
    transform: translateX(-100%);
  }
}

@-webkit-keyframes moveToRight {
  from {
  }
  to {
    -webkit-transform: translateX(100%);
  }
}

@keyframes cartOut {
  from {
    transform: translate(0px, 0px);
  }
  to {
    transform: translate(1200px, 0px);
    animation-timing-function: ease-out;
  }
}

@-webkit-keyframes moveToLeft {
  from {
  }
  to {
    opacity: 0.5;
    -webkit-transform: translateX(-100%);
  }
}

@keyframes moveToLeft {
  from {
  }
  to {
    opacity: 0.5;
    -webkit-transform: translateX(-100%);
    transform: translateX(-100%);
  }
}

@-webkit-keyframes moveFromRight {
  from {
    opacity: 0.7;
    -webkit-transform: translateX(100%);
  }
}

@keyframes moveFromRight {
  from {
    opacity: 0.7;
    -webkit-transform: translateX(100%);
    transform: translateX(100%);
  }
}

.drawer-closer .item-content {
  margin-left: 50px !important;
}

.drawer-content .list-label {
  line-height: 45px;
}

.drawer-content .item {
  height: 45px;
}

.router-link-active .item-primary {
  color: #027be3;
}

@media only screen and (min-width: 601px) {
  .adv-form-one .timeline-badge {
    right: auto !important;
    left: auto !important;
  }

  .adv-form-one .timeline-content {
    margin-left: 3.9rem;
  }

  .adv-form-one .timeline-item {
    width: 100% !important;
  }

  .adv-form-one .timeline-title {
    text-align: inherit !important;
    margin-left: 3.9rem;
  }

  .timeline:before {
    left: 1.6rem;
  }
}

.adv-form-one .timeline-content .group .primary {
  display: none !important;
}

.underline {
  text-decoration: underline;
}

input[type='checkbox'] {
  accent-color: grey;
}

/*for side bar fix css */

.forSideBar {
  position: absolute;
  top: 52px;
  left: 0px;
  z-index: 9999999999999;
  display: block;
  min-height: 100vh;
  height: 100%;
  width: 250px;
  /* width: 17.7%; */

}

.forContent {
  padding-left: 260px;
  padding-top: 10px;
}

/*.forContent > .mapboxgl-control-container >  maplibregl-ctrl-top-left {*/
/*    top: 45px;*/
/*    left: 0;*/
/*    right: 10px;*/
/*    left: unset;*/
/*}*/
/*.mapboxgl-ctrl-top-left{*/
/*  top: 45px;*/
/*    left: 0;*/
/*    right: 10px;*/
/*    left: unset;*/

/*}*/
div#markmap .mapboxgl-control-container .mapboxgl-ctrl-top-left {
  top: 45px !important;
  left: 0 !important;
  right: 10px !important;
  left: unset !important;

}

.menuLink {
  color: white;
  background: #F2C037
}

.toolbarSpace {
  margin-bottom: 0px;
}

@media (max-width: 992px) {
  .forSideBar {
    width: 200px;
  }

  .forSideBar .q-item {
    min-height: 45px;
    /*padding: 8px 10px;*/

  }

  .forSideBar aside {
    width: 100% !important;

  }

  .q-item.q-item-type.row.no-wrap.q-item--clickable.q-link.q-item--active.activeClass {
    width: 180px;
    margin-left: 0px !important;
    padding-left: 10px !important;
  }

  .q-item.q-item-type.row.q-item--active.activeClass {
    height: 40px !important;
  }

  .activeClass {

    transform: translate(2px, 5px);

  }


  div#forContent {
    padding-left: 215px !important;
  }

  div#forContent .q-layout-container {
    width: 98% !important;
  }

  .forSideBar .q-item__section--side > .q-icon {
    font-size: 22px;
  }

  .forSideBar .q-item__section--main ~ .q-item__section--side {

    transform: translate(-45px, 0px);
  }

  .forSideBar .q-expansion-item__container .q-item {

    padding: 8px 5px !important;

  }

  .q-item.q-item-type.row.no-wrap.q-item--clickable {
    padding: 0 5px;
  }

  .q-item__section.column.q-focusable.q-item__section--side {
    transform: translate(-60px, 0px);
  }

  .q-item {

    padding: 8px 5px;

  }

  .forSideBar .q-list--padding {

    width: 80%;
  }
}


</style>

<style lang="sass">
.my-menu-link
  color: white
  background: #F2C037
  border-radius: 30%
</style>

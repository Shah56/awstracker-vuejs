<template>
  <div class="column justify-center q-pa-lg forPadding"
       style="background-color: #40444f; width: 100%; position:fixed !important;">
    <!-- <q-card square class="shadow-24" style="width:300px;height:485px;"> -->
    <div class="stealthMain">
      <div class="stealthLeft">
        <h2 class="stealthHeading">STEALTH CONNECT</h2>
        <h5 style="font-family: 'arial'; margin-top: 10px; font-size: 1.75rem; color: white">Cyber Security Portal</h5>
        <p style="font-size: 1.25rem; color: white">Introducing TOM SHAW’s latest creation: Stealth Connect. A
          two-part cyber-security <br/> world-first protecting
          governments and <br/> enterprises from the end point to the board room.</p>
      </div>
      <div class="stealthMiddle">
        <img src="https://noble1webapp.s3.ap-southeast-2.amazonaws.com/img/center-bg.png" alt="midImage"
             class="backImage"/>
        <div class="learnMoreSignIn">
          <div class="innerCircle">
            <p style="margin-top: -15px;">Learn More</p>
          </div>
        </div>
      </div>
      <div class="stealthRight">
        <q-card-section style="margin-bottom: 20px">
          <h4 class="text-h4 text-center q-my-sm" style="color: white">Login Your Account</h4>
        </q-card-section>

        <q-card square class="shadow-24" style="width:100%;padding: 50px 20px; background-color: #40444f !important;">

          <q-card-section>
            <q-form>
              <q-input
                  class="firstInput"
                  input-style="padding-left:10px;"
                  outlined
                  color="white"
                  dark
                  standout
                  input-class="q-pl-sm"
                  v-model="form.username"
                  label-color="grey"
                  bg-color="transparent"
                  v-model.trim="form.username"
                  label="Email"
                  @blur="$v.form.username.$touch"
                  error-message="Please use a valid email"
                  :error="$v.form.username.$error"
              >
                <template v-slot:prepend>
                  <q-icon name="email" style="color: white;"/>
                </template>
                <template v-slot:append>
                  <q-icon name="cancel" @click.stop.prevent="form.username = null" class="cursor-pointer"
                          style="color: white"/>
                </template>
              </q-input>
              <q-input
                  outlined
                  color="white"
                  input-style="padding-left:10px;"
                  dark
                  label-color='grey'
                  bottom-slots
                  bg-color="transparent"
                  v-model="form.password"
                  type="password"
                  :dense="dense"
                  label="Password"
                  error-message="Password Invalid"
                  @blur="$v.form.password.$touch"
                  :error="$v.form.password.$error"
              >
                <template v-slot:prepend>
                  <q-icon name="lock" style="color: white"/>
                </template>
                <template v-slot:append>
                  <q-icon name="cancel" @click.stop.prevent="form.password = null" class="cursor-pointer"
                          style="color: white"/>
                </template>
              </q-input>
            </q-form>
          </q-card-section>
          <q-card-section class="text-center q-pa-sm" v-if="hasLoginError">
            <q-btn size="sm" color="red" icon="highlight_off" :label="loginError" @click="hasLoginError=false"/>
          </q-card-section>
          <q-card-actions class="q-px-lg">
            <q-btn
                rounded unelevated
                size="lg"
                @click="onSubmit"
                class="bg-primary half-width text-white"
                style="background-color: grey !important; padding: 0 20px 0px 20px"
                label="Log In"
            />
            <p
                @click="signUp"
                class="signUp"
            >Sign Up</p>
          </q-card-actions>
          <q-card-section class="text-center q-pa-sm">
            <q-btn flat size="sm" @click="forgotPassword" color="white" label="Forgot you password?"/>
            <!--            <q-separator/>-->
            <!--            <q-btn flat size="sm" @click="signUp" color="black" label="Don't have an account? Sign Up here!"/>-->
          </q-card-section>
        </q-card>
      </div>
    </div>


  </div>
</template>

<script>
import {Auth} from "aws-amplify";
import {AmplifyEventBus} from "aws-amplify-vue";
import {email, required} from 'vuelidate/lib/validators';
import {ref} from "vue";

export default {
  name: "SignIn",
  /**
   * @param {string} redirectTo - Sets Route one must go once authenticated
   */
  props: {
    redirectTo: String
  },
  setup() {
    return {
      dense: ref(false)
    }
  },
  data() {
    return {
      hasLoginError: false,
      loginError: '',
      form: {
        username: "",
        password: ""
      }
    };
  },
  validations: {
    form: {
      username: {required, email},
      password: {required},
    }
  },
  methods: {
    async onSubmit() {
      this.loginError = '';
      this.hasLoginError = false;
      this.$v.form.$touch()
      if (this.$v.form.$pending || this.$v.form.$error) {
        return
      }
      const {username, password} = this.form;
      try {
        const user = await Auth.signIn(username, password);
        console.log(user.username)
        AmplifyEventBus.$emit("authState", "signedIn");
        this.$router.push("/");
      } catch (error) {
        this.loginError = error.message
        this.hasLoginError = true;
      }
    },
    signUp() {
      this.$router.push("/signup");
    },
    forgotPassword() {
      this.$router.push("/forgotpassword");
    }
  }
};
</script>
<style scoped>
.forPadding {
  padding: 0 120px 100px;
}

.stealthMain {
  display: flex;
  justify-content: space-between;
  /*align-items: center;*/
  gap: 5%;
}

.stealthLeft {
  width: 40%;
  padding-top: 120px;
}

.stealthMiddle {
  width: 30%;
  position: relative;
}

.inputText {
  font-size: 32px;
}

.stealthRight {
  width: 40%;
  /*margin-top: -70px;*/
  padding-top: 120px;
}

.signUp {
  font-size: 20px;
  margin-left: 30px;
  margin-top: 10px;
  cursor: pointer;
  color: white;
}

.inputValColor {
  color: white;
}

.stealthHeading {
  font-family: 'Agency Gothic CT Bold';
  margin-bottom: 0px;
  font-size: 70px;
  font-weight: 500;
  color: white
}

.learnMoreSignIn {
  display: inline-block;
  /* margin-top: -681px; */
  /* margin-right: 80px; */
  border-radius: 50%;
  /* padding: 65px; */
  color: white;
  border: 1px solid white;
  font-size: 35px;
  background-color: #40444f;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-62%, -29%);
  height: 255px;
  width: 255px;
  text-align: center;
  padding-top: 95px;
}

.innerCircle {
  display: inline-block;
  /* margin-top: -681px; */
  /* margin-right: 80px; */
  border-radius: 50%;
  /* padding: 65px; */
  color: white;
  border: 10px solid grey;
  font-size:25px;
  background-color: #40444f;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  height: 211px;
  width: 211px;
  text-align: center;
  padding-top: 95px;
}


.backImage {
  width: 70%;
  height: 110%;
  margin-left: 20px;
  /*margin-top: -120px*/
}

.q-btn .q-focus-helper {
  display: none;
}

.q-field__control-container.col.relative-position.row.no-wrap.q-anchor--skip {
  padding-left: 10px !important;
  background-color: transparent !important;
}

.q-field__label.no-pointer-events.absolute.ellipsis.text-grey {
  padding-left: 10px;
}

.firstInput q-input {
  padding-left: 12px !important;
}

.q-field__before, .q-field__prepend {
  /* padding-right: 12px; */
  width: 35px;
  background: red !important;
}

</style>
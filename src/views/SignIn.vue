<template>
  <div class="column justify-center q-pa-lg forPadding" style="background-color: #181414">
    <!-- <q-card square class="shadow-24" style="width:300px;height:485px;"> -->
    <div class="stealthMain">
      <div class="stealthLeft">
        <h2 class="stealthHeading">STEALTH CONNECT</h2>
        <h5 style="font-family: 'arial'; margin-top: 10px; font-size: 1.75rem; color: white">Cyber Security Portal</h5>
        <p style="font-size: 1.25rem; color: white">Introducing TOM SHAW’s latest creation: Stealth Connect. <br/> A
          two-part cyber-security world-first protecting
          governments <br/> and enterprises from the end point to the board room.</p>
      </div>
      <div class="stealthRight">
        <q-card-section style="margin-bottom: 20px">
          <h4 class="text-h4 text-center q-my-sm" style="color: white">Login Your Account</h4>
        </q-card-section>

        <q-card square class="shadow-24" style="width:100%;padding: 50px 30px; background-color: #181414 !important;">

          <q-card-section>
            <q-form>
              <q-input
                  square outlined
                  color="white"
                  dark
                  label-color="grey"
                  bg-color="transparent"
                  v-model.trim="form.username"
                  label="Email"
                  @blur="$v.form.username.$touch"
                  error-message="Please use a valid email"
                  :error="$v.form.username.$error"
              >
                <template v-slot:prepend>
                  <q-icon name="email" style="color: white"/>
                </template>
                <template v-slot:append>
                  <q-icon name="cancel" @click.stop.prevent="form.username = null" class="cursor-pointer"
                          style="color: white"/>
                </template>
              </q-input>
              <q-input
                  square outlined
                  color="white"
                  dark
                  label-color='grey'
                  standout
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
                <template v-slot:hint>
                  Email
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
import {required, email} from 'vuelidate/lib/validators';
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
  padding: 120px 120px;
}

.stealthMain {
  display: flex;
  justify-content: space-between;
  /*align-items: center;*/
  gap: 5%;
}

.stealthLeft {
  width: 50%;
}

.inputText {
  font-size: 32px;
}

.stealthRight {
  width: 35%;
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
</style>
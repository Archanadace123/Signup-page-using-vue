<template>
  <v-app>
    <v-container fluid class="d-flex justify-center align-center fill-height">
      <v-row align="center" justify="start">
        <v-col sm="6">
          <v-spacer></v-spacer>
          <v-img
            lazy-src="@/assets/img2.jpg"
            contain
            src="@/assets/img2.jpg"
          ></v-img>
        </v-col>
        <v-divider> vertical</v-divider>
        <v-col sm="6">
          <v-spacer></v-spacer>
          <v-card class="elevation-24 mx-12" min-width="400">
            <v-toolbar color="#64B5F6" dark flat>
              <v-toolbar-title
                class="
                  text-uppercase
                  font-weight-bold
                  hidden-sm-and-down
                  mx-auto
                "
                >CREATE YOUR ACCOUNT</v-toolbar-title >
            </v-toolbar>

            <v-card-text>
              <v-form ref="form" v-model="valid" lazy-validation>
                <v-text-field
                  prepend-icon="mdi-account"
                  v-model="name"
                  label="Name"
                >
                </v-text-field>
                <v-text-field
                  prepend-icon="mdi-email"
                  v-model="email"
                  label="E-mail"
                  :rules="emailRules"
                  required
                ></v-text-field>
                <v-text-field
                  prepend-icon="mdi-phone"
                  v-model="phonenumber"
                  label="Phone number"
                ></v-text-field>
                <div
                  fluid
                  class="d-flex justify-center align-center fill-height"
                >
                  <v-btn
                    color="#64B5F6"
                    dark
                    flat
                    class="
                      text-uppercase
                      font-weight-bold
                      hidden-sm-and-down
                      mx-auto
                    "
                  >
                    Sign Up
                  </v-btn>
                </div>

                <v-checkbox
                  v-model="checkbox"
                  :label="`I agree to all the terms and conditions`"
                ></v-checkbox>
                <template>
                  <v-container
                    fluid
                    class="d-flex justify-center align-center fill-height"
                  >
                    <div>
                      Already have an account
                      <v-tooltip bottom>
                        <template v-slot:activator="{ on }">
                          <a
                            target="_blank"
                            href="https://vuetifyjs.com"
                            @click.stop
                            v-on="on"
                          >
                            Login?
                          </a>
                        </template>
                        Opens in new window
                      </v-tooltip>
                    </div>
                  </v-container>
                </template>
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>
 
<script>
export default {
  data() {
    return {
      userData: {
        valid: true,
        name: "",
        email: "",
        emailRules: [
          (v) => !!v || "E-mail is required",
          (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
        ],
        password: "",
        phonenumber: "",
        checkbox: true,
      },
    };
  },
  methods: {
    submitted() {
      this.isSubmitted = true;
    },
    validate() {
      this.$refs.form.validate();
    },
  },
};
</script>


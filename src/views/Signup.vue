<template>
  <v-app>
    <v-content>
      <v-container>
        <v-layout wrap>
          <v-flex xs12 sm8 md6>
            <form>
              <v-text-field
                v-model="name"
                :error-messages="nameErrors"
                :counter="10"
                clearable
                label="Name"
                required
                @input="$v.name.$touch()"
                @blur="$v.name.$touch()"
              />
              <v-text-field
                v-model="email"
                :error-messages="emailErrors"
                clearable
                label="E-mail"
                required
                @input="$v.email.$touch()"
                @blur="$v.email.$touch()"
              />

              <v-text-field
                v-model="password"
                :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                :rules="[rules.required, rules.min]"
                :type="show1 ? 'text' : 'password'"
                clearable
                name="input-10-1"
                label="Password"
                hint="At least 8 characters"
                counter
                @click:append="show1 = !show1"
              />

              <v-btn class="mr-4" @click="submit">
                sign up
              </v-btn>
              <Googleauth />
            </form>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required, maxLength, email } from 'vuelidate/lib/validators'

import Googleauth from '../components/Googleauth'

export default {
  components: { Googleauth },
  mixins: [validationMixin],
  validations: {
    name: { required, maxLength: maxLength(10) },
    email: { required, email }
  },
  data: () => ({
    name: '',
    email: '',
    show1: false,
    password: '',
    rules: {
      required: value => !!value || 'Required.',
      min: v => v.length >= 8 || 'Min 8 characters',
      emailMatch: () => "The email and password you entered don't match"
    }
  }),

  computed: {
    nameErrors() {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength &&
        errors.push('Name must be at most 10 characters long')
      !this.$v.name.required && errors.push('Name is required.')
      return errors
    },
    emailErrors() {
      const errors = []
      if (!this.$v.email.$dirty) return errors
      !this.$v.email.email && errors.push('Must be valid e-mail')
      !this.$v.email.required && errors.push('E-mail is required')
      return errors
    }
  },

  methods: {
    submit() {
      this.$v.$touch()
    },
    clear() {
      this.$v.$reset()
      this.name = ''
      this.email = ''
    }
  }
}
</script>

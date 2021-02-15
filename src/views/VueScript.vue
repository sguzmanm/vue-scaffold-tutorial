<template>
  <div>
    <p>
      Mi nombre es: <b>{{firstname}} {{lastname}}</b>
    </p>
    <v-form v-model="valid">
      <v-container>
        <v-row>
          <v-col
            cols="12"
            md="4"
          >
            <v-text-field
              v-model="firstname"
              :counter="length"
              label="First name"
              required
            ></v-text-field>
          </v-col>

          <v-col
            cols="12"
            md="4"
          >
            <v-text-field
              v-model="lastname"
              :counter="length"
              label="Last name"
              required
            ></v-text-field>
          </v-col>

          <v-col
            cols="12"
            md="4"
          >
            <v-btn
              color="warning"
              @click="()=>{resetInputs()}"
            >
              Reset Inputs
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </div>
</template>
<style scoped>
</style>
<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component({})

export default class VueScript extends Vue {
  valid = false

  firstname = ''

  lastname = ''

  length = 10

  resetInputs() {
    this.valid = false;
    this.firstname = '';
    this.lastname = '';
  }

  mounted() {
    this.firstname = 'Checho';
  }
}
</script>

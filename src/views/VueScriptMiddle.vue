<template>
  <div>
    <p>
      Mi nombre es: <b>{{fullName}}</b>
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
              color="success"
              @click="()=>{addName()}"
            >
              Add Name
            </v-btn>
          </v-col>
        </v-row>
        <v-row>
          <v-col
            cols="12"
            md="4"
          >
            <v-checkbox
              v-model="showNames"
              label="Show Names?">
            </v-checkbox>
          </v-col>
        </v-row>

      </v-container>
    </v-form>
    <ul v-if="showNames">
      <li v-for="(item,index) in names" :key="index">
        {{index+1}}. {{item}}
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
import { Vue, Component, Watch } from 'vue-property-decorator';

@Component({})

export default class VueScript extends Vue {
  valid = false

  showNames = false

  firstname = ''

  lastname = ''

  length = 10

  names: string[] = []

  // Declared as computed property getter
  get fullName() {
    return `${this.firstname} ${this.lastname}`;
  }

  // Declared as computed property setter
  set fullName(value) {
    const splitted = value.split(' ');
    let lastname: string;
    [this.firstname, lastname] = splitted;

    if (!lastname) {
      lastname = '';
    }

    this.lastname = lastname;
  }

  @Watch('showNames')
  onPropertyChanged(value: boolean, oldValue: boolean) {
    // Do stuff with the watcher here.
    if (value && !oldValue) {
      fetch('https://checho.requestcatcher.com/').then(() => console.log('Hola'));
    }

    console.log(this.showNames);
  }

  addName() {
    this.names.push(this.fullName);
    this.fullName = '';
  }

  mounted() {
    this.firstname = 'Checho';
  }
}
</script>

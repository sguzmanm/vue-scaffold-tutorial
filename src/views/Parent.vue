<template>
  <div class="parent">
    <input v-model="inputText" placeholder="Put your text here">
    <child-component @updateText="updateInputText" :inputText="inputText"/>
  </div>
</template>
<style scoped>
.parent{
  border: black solid 1px;
  padding: 5px;
}

.parent input{
  border: grey 1px solid;
  margin-bottom: 20px;
}
</style>
<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';
import ChildComponent from '@/components/ChildComponent.vue';

@Component({
  components: {
    ChildComponent,
  },
})

export default class Parent extends Vue {
  inputText=''

  updateInputText(reverseText: string) {
    console.log(reverseText);
    this.inputText = reverseText;
    alert(`Input text has been updated ${this.inputText}`);
  }
}
</script>

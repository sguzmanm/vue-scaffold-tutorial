<template>
  <div class="child">
    <button @click="makeReverse">Reverse</button>
  </div>
</template>
<style scoped>
.child{
  border: greenyellow solid 1px;
  padding: 5px;
    opacity: 50%;
    background: green;
}

.child button{
  border:black 1px solid;
  padding: 2px;
}

.child button:hover{
  background: greenyellow;
}

</style>
<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';

@Component({})

export default class ChildComponent extends Vue {
  @Prop({ required: true })
  inputText!: string

  makeReverse() {
    console.log(this.inputText.split('').reverse().join(''));
    this.$emit('updateText', this.inputText.split('').reverse().join(''));
  }
}
</script>

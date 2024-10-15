<script setup>
import { ref } from 'vue';


const count = ref([0,0,0,0,0,0,0,0])
const frequency = ref([0,0,0,0,0,0])
const len = ref(8)

const throwDice = () => {
  count.value = Array.from({ length: len.value }, () => Math.ceil(Math.random() * 6));
  count.value.sort((a, b) => a - b)
  frequency.value = [0,0,0,0,0,0]
  for (let i = 0; i < count.value.length; i++) {
  frequency.value[count.value[i]-1]++;
}
};
</script>

<template>
  <h1>DiceVue3</h1>

  <div class="card">
    <button type="button" @click="throwDice">Throw dice</button><br>
    <input type="number "v-model="len">
    <table>
      <tr>
        <th>Dice Value</th>
        <td>1,</td>
        <td>2,</td>
        <td>3,</td>
        <td>4,</td>
        <td>5,</td>
        <td>6</td>
        <th>Expected</th>
      </tr>
      <tr>
        <th>Frequency</th>
        <td>{{ frequency[0] }},</td>
        <td>{{ frequency[1] }},</td>
        <td>{{ frequency[2] }},</td>
        <td>{{ frequency[3] }},</td>
        <td>{{ frequency[4] }},</td>
        <td>{{ frequency[5] }},</td>
        <td>{{ (len / 6).toFixed(2) }}</td>
      </tr>
      <tr>
        <th>Off-set</th>
        <td>{{ frequency[0]*6/len }}</td>
        <td>{{ frequency[1]*6/len }}</td>
        <td>{{ frequency[2]*6/len }}</td>
        <td>{{ frequency[3]*6/len }}</td>
        <td>{{ frequency[4]*6/len }}</td>
        <td>{{ frequency[5]*6/len }}</td>
      </tr>
    </table>
    <p>
      Dice thrown: {{ count }}
    </p>
    
  </div>
</template>


<style scoped>
.read-the-docs {
  color: #888;
}
</style>

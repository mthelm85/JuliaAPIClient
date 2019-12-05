<template>
  <v-container>
    <v-row
      text-center
      align="center"
      justify="center"
      row
      wrap>
      <v-col align="center" justify="center" xs2>
        <v-text-field
        outlined
        placeholder="X"
        v-model="x"
        hide-details
        single-line
        height="100px"
        type="number"
        class="inputs">
        </v-text-field>
      </v-col>
      <v-col align="center" justify="center" xs2>
        <span class="display-4">+</span>
      </v-col>
      <v-col align="center" justify="center" xs2>
        <v-text-field
        outlined
        placeholder="Y"
        v-model="y"
        hide-details
        single-line
        height="100px"
        type="number"
        class="inputs">
        </v-text-field>
      </v-col>
      <v-col align="center" justify="center" xs4>
        <span class="display-4">=</span>
      </v-col>
      <v-col align="center" justify="center" xs2>
        <span class="display-4">{{ answer }}</span>
      </v-col>
      <v-col align="center" justify="center" xs2>
        <v-btn @click="getAnswer">Compute</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',

  data: () => ({
    x: null,
    y: null,
    answer: null
  }),

  methods: {
    async getAnswer() {
      try {
        this.answer = await axios.get('https://julia-api-example.herokuapp.com/addxy', {
          params: {
            x: this.x,
            y: this.y
          }
        })
      } catch (err) {
        alert(err)
      }
    }
  }
}
</script>
<style scoped>
.inputs {
  font-size: 36px;
  width: 80px;
}
</style>

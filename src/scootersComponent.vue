<template>
<div>
    <div class="tools">
        <button @click="ga">Test</button>
        <span>Antal scooters: {{numberOfScooters}}</span>
        <button @click="sortScooterByDistanceToYou">Sort by distance</button>
    </div>
  <div class="list">
      <table>
        <tr>
          <th>ID</th>
          <th>Distance from you</th>
        </tr>
        <tr v-for="scooter,index in as" :key="index">
            <td>{{scooter.scooter_id}}</td>
            <td>{{scooter.distance}} km</td>
        </tr>
      </table>
  </div>
</div>
</template>

<script>
import data from '../scooter_mock_data'

export default {
    data() {
        return {
            as: [],
            maxDist: 1,
            numberOfScooters: null
        }
    },
    methods: {
        getScooters() {
            this.as = data
            this.numberOfScooters = this.as.length
        },
        ga() {
            console.log("ga!")
            const fl = []
            const s = this.as
            for (let i=0; i<s.length;i++) {
                const si = {...s[i], wr: (s[i].distance < this.maxDist && s[i].available)}
                s[i] = si
                for (let j=0;j<s.length;j++) {
                    fl.push(si.wr ? si : null)
                    this.as = fl
                    this.numberOfScooters = j
                }
            }
        },
        sortScooterByDistanceToYou() {
            // TODO: implement this

        }
    },
    mounted() {
        this.getScooters()
    }
}
</script>

<style>
.tools {
    display: flex;
    justify-content: space-between;
    padding: 30px;
    background: #f1f1f1;
    border-radius: 10px;
}
table {
    margin: 20px;
}
</style>
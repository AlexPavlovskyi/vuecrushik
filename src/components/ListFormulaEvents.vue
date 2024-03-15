<template>
  <div>
    <header>
      <h1 class="title inter">F1 Events this season 🏁🏎️</h1>
    </header>
    <div class="events" v-if="events && events.MRData">
      <div class="event" v-for="(race, index) in events.MRData.RaceTable.Races" :key="index">
        <table>
          <tr class="tableTitle">
            <th colspan="2"><h2>{{ race.raceName }} - {{ race.Circuit.Location.locality }}, {{ race.Circuit.Location.country }}</h2></th>
          </tr>
          <tr v-for="(practice, practiceName) in race" :key="practiceName">
            <td v-if="['FirstPractice', 'SecondPractice', 'ThirdPractice', 'Qualifying'].includes(practiceName)" style="width: 50%;">{{ practiceName }}</td>
            <td v-if="['FirstPractice', 'SecondPractice', 'ThirdPractice', 'Qualifying'].includes(practiceName)" style="width: 50%;">{{ 
            formatDate(practice) }}</td>
          </tr>
          <tr v-if="showRaceButton(race)">
            <td colspan="2" style="width: 100%; text-align: center;">
              <button @click="showRaceResultPopup(race.round, race.season)" :style="{ background: 'green'}" class="btn">Race Result</button>
            </td>
          </tr>
        </table>
      </div>
    </div>
    <RaceResult v-if="showRaceResult" :eventRound="selectedRound" :eventYear="selectedYear" @close="showRaceResult = false" />
  </div>
</template>

<script>
import RaceResult from './RaceResult.vue';

export default {
  name: 'ListFormulaEvents',
  components: {
    RaceResult
  },
  data() {
    return {
      events: {},
      showRaceResult: false,
      selectedRound: null,
      selectedYear: null
    };
  },
  methods: {
    async fetchEvents() {
      try {
        const response = await fetch('http://ergast.com/api/f1/current.json');
        const data = await response.json();
        return data;
      } catch (error) {
        console.log(error);
      }
    },
    async update() {
      this.events = await this.fetchEvents();
    },
    showRaceResultPopup(round, year) {
      this.selectedRound = round;
      this.selectedYear = year;
      this.showRaceResult = true;
    },
    showRaceButton(race) {
      const currentDate = new Date();
      const raceDate = new Date(race.date);
      return raceDate < currentDate; // Показувати кнопку лише якщо дата гонки вже минула
    },
    formatDate(practice) {
      const currentDate = new Date();
      const practiceDate = new Date(`${practice.date}T${practice.time}`);
      if (practiceDate > currentDate) {
        return `${practiceDate.toLocaleString()}`;
      } else {
        return 'Already happened';
      }
    }
  },
  async created() {
    await this.update();
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.title {
  font-size: 32px;
  text-align: center;
  }
.inter {
  font-family: "Inter", sans-serif;
  font-optical-sizing: auto;
  font-weight: 700;
  font-style: normal;
  font-variation-settings:
  "slnt" 0;
  color: white;
}
button {
  font-size: 12px;
  padding: 0px 13px;
  
}
.events {
  background: darkolivegreen;
  /* background: #284875; */
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 230px;
  border-radius: 8px;
  padding: 20px 30px;
  margin-bottom: 10px;
  margin-top: 10px;
}
.event{
  margin-left: 0;

}
table {
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
  min-width: 500px;
  width: 100%; /* розширює таблицю на всю ширину */
}
td {
  background: #404741;
  padding: 5px 20px;
  cursor: pointer;
  border-radius: 8px;
  width: 100%; /* розширює кожен рядок на всю ширину */
  text-align: center;
}
td:hover{
  background: #374039;
}
th {
  background: #2b302c;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
  color: white;
  min-width: 500px;
  
}
</style>

<template>
  <div class="modal" v-if="showModal">
    <div class="modal-content">
      <span class="close" @click="closeModal">&times;</span>
      <h1 class="title inter">Race Results 🏆</h1>
      <table>
        <tr>
          <th>Position</th>
          <th>Driver</th>
          <th>Constructor</th>
          <th>Laps</th>
          <th>Time</th>
          <th>Points</th>
        </tr>
        <tr v-for="(result, index) in results" :key="index">
          <td>{{ result.position }}</td>
          <td>{{ result.Driver.givenName }} {{ result.Driver.familyName }}</td>
          <td>{{ result.Constructor.name }}</td>
          <td>{{ result.laps }}</td>
          <td v-if="result.status === 'Finished'">{{ result.Time.time }}</td>
          <td v-else>{{ result.status }}</td>
          <td>{{ result.points }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: ['eventYear', 'eventRound'],
  data() {
    return {
      showModal: true,
      results: null
    };
  },
  methods: {
    async fetchResults() {
      try {
        const response = await fetch(`http://ergast.com/api/f1/${this.eventYear}/${this.eventRound}/results.json`);
        const data = await response.json();
        this.results = data.MRData.RaceTable.Races[0].Results;
      } catch (error) {
        console.log(error);
      }
    },
    closeModal() {
      this.showModal = false;
      this.$emit('close');
    }
  },
  async created() {
    await this.fetchResults();
  }
};
</script>

<style scoped>
.modal {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal-content {
  background-color: rgba(128, 0, 0, 0.9);
  padding: 20px;
  border-radius: 10px;
  width: 50%;
  overflow-y: auto; /* Дозволяє вертикальну прокрутку за потреби */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  align-items: center;
  max-height: 80%;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
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
  padding-right: 15px;
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
  margin-left: 30px;
}
.events {
  background: #78242a;
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
}
td{
  background: #404741;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
}
td:hover{
  background: #374039;
}
th{
  background: #2b302c;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
  color: white;
}
/* Для всього скролбара */
.modal-content::-webkit-scrollbar {
  width: 12px;
  border-radius: 10px; /* Заокруглення скролбара */
}

/* Для стрілок скролбара */
.modal-content::-webkit-scrollbar-button {
  background: #555;
}

/* Для треку скролбара */
.modal-content::-webkit-scrollbar-track {
  background: #888;
  border-radius: 10px; /* Заокруглення треку скролбара */
}

/* Для полоски скролбара */
.modal-content::-webkit-scrollbar-thumb {
  background: #bbb;
  border-radius: 10px; /* Заокруглення підбірки скролбара */
}

/* Для полоски скролбара при наведенні */
.modal-content::-webkit-scrollbar-thumb:hover {
  background: #aaa;
}

/* Для краю скролбара при початку */
.modal-content::-webkit-scrollbar-corner {
  background: #ccc;
}

</style>


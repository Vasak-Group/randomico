<script>
import WinnerAnnouncement from '../components/WinnerAnnouncement.vue'

export default {
  data() {
    return {
      premio: "",
      text: "",
      winner: "",
      selected: false,
    }
  },
  methods: {
    async sortear() {
      const list = this.text.split("\n")
      const random = Math.floor(Math.random() * list.length);
      this.winner = list[random]
      this.selected = true
    },
    close() {
      this.selected = false
    }
  },
  name: 'HomeView',
  components: {
    WinnerAnnouncement
  },
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-12 text-center">
        <h1>Sorteo Simple</h1>
      </div>

      <div class="col-12 text-center">
        <div class="mb-3">
          <input class="form-control" type="text" v-model="premio" placeholder="Premio" />
        </div>
      </div>

      <div class="col-md-8">
        <div class="mb-3">
          <textarea v-model="text" class="form-control" rows="10"></textarea>
        </div>
      </div>

      <div class="col-md-4 text-center">
        <button class="btn btn-primary" @click="sortear()">
          Sortear
        </button>
      </div>
    </div>
    <WinnerAnnouncement @close="close()" v-if="selected" :winner="winner" :premio="premio" v-bind:selected="selected" />
  </div>
</template>

<style scoped>
h1 {
  margin-bottom: 20px;
}

.btn {
  height: calc(100% - 1rem);
  width: 100%;
  padding: 1rem;
  padding-bottom: 2rem;
  border-radius: var(--border-radius);
  font-size: 30px;
  font-weight: bold;
  background: var(--accent-color);
  border: 0px;
}

.btn:hover {
  background: var(--accent-color-dark);
  border: 0px;
}

textarea,
input {
  border-radius: var(--border-radius);
}
</style>
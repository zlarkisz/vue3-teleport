<template>
  <h1>{{ title }}</h1>

  <p>Welcome...</p>

  <teleport to="#modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template #links>
        <a href="#">sign in now</a>
        <a href="#">more info</a>
      </template>

      <h1>Sign up for the Giveaway</h1>
      <p>Grab your ninja swag for half price !</p>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Sign up for the newsletter</h1>
      <p>for updates and promocodes !</p>
    </Modal>
  </teleport>

  <button @click="toggleModal">open modal</button>
  <button @click="toggleModalTwo">open modal</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',

  components: {
    Modal,
  },

  data() {
    return {
      title: 'My first Vue3 app :)',
      showModal: false,
      showModalTwo: false
    }
  },

  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  },
}
</script>

<style>
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

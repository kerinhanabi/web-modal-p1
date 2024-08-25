<template>
  <h1>{{ title }}</h1>
  <!--input type="text" ref="name"-->
  <p>Welcome...</p>

  <!-- // simple example 1 // -->
  <!--button @click="handleClick">click me</button-->
  <!--Modal header="Sign up for the Giveaway!" text="Grab your device for half price!"/-->
  
  <!-- // simple example 2 : prop // -->
  <!--div v-if="showModal">
    <Modal :header="header2" :text="text2" theme="sale" @close="toggleModal"/--> <!-- another way of v-bind modal -->
  <!--/div-->

  <!-- // simple example 3 : slot // -->
  <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <h1>Example 03 : Slot</h1>
      <p>Description for example 03</p>
      <template #links>
        <a href="#">Sign Up Now</a>
        <a href="#">More info</a>
      </template>
    </Modal>
  </div>
<!-- exercise challenge to create ModalTwo -->

  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <h1>Challenge create Modal Two</h1>
      <p>Challenge create modal two</p>
    </Modal>
  </div>

  <!-- using teleport feature to open ModalThree in a div.modals in index.html -->
  <!-- check it on browser inspect elements to see difference compare to default example showModal above -->
  <Teleport to="#modals" v-if="showModalThree"> <!-- change to=".modals" if is using class name instead of id name -->
    <Modal @close="toggleModalThree">
      <h1>Challenge create Modal Three</h1>
      <p>Challenge create modal 3</p>
    </Modal>
  </Teleport>

  <button @click="toggleModal">open modal</button>
  <button @click="toggleModalTwo">open modal 2</button> <!-- challenge to open ModalTwo -->
  <button @click="toggleModalThree">open modal 3</button> <!-- open modals using telepot feature in vue -->
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My first Vue App :)',
      header2: '2: Sign up for the Giveaway!',
      text2: '2: Grab your device for half price!',
      showModal: false,
      showModalTwo: false,
      showModalThree: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    },
    toggleModalThree() {
      this.showModalThree = !this.showModalThree
    }
  }
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
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>

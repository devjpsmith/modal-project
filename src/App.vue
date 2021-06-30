<template>
  <h1>{{ title }}</h1>
  <div v-if="showModal">
    <Modal theme="sale" @close="() => showModal = false">
      <h1>Super Giveaway</h1>
      <p>Grab your stuff NOW!</p>
      <template v-slot:links>
        <a href="#">Gift 1</a>
        <a href="#">Gift 2</a>
        <a href="#">Gift 3</a>
      </template>
    </Modal>
  </div>
  <div v-if="showMyModal">
    <Modal id="myModal" @close="() => showMyModal = false">
      <h1>My Modal</h1>
      <p>This is a plain modal</p>
    </Modal>
  </div>
  <button id="openModalBtn" @click="toggleModal($event)">Open Modal</button>
  <br>
  <button id="openMyModalBtn" @click="toggleModal($event)">Open My Modal</button>
</template>

<script>
import Modal from './components/Modal';

export default {
  name: 'App',
  components: {
    Modal,
  },
  data() {
    return {
      title: 'Modal App',
      showModal: false,
      showMyModal: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active');
      this.$refs.name.focus();
    },
    toggleModal(e) {
      if (e && e.srcElement?.id === 'openMyModalBtn') {
        console.log(e);
        this.showMyModal = !this.showMyModal;
      } else {
        this.showModal = !this.showModal;
      }
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  align-items: center;
}

h1 {
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}

.active {
  border: 5px solid #2d8149;
}

button {
  border: none;
  min-width: 200px;
  font-weight: bold;
  text-transform: uppercase;
  height: 30px;
  margin-bottom: 10px;
  border-radius: 4px;
  color: #ddd;
  background-color: #333;
}

</style>

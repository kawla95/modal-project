<!-- each vue component must at least have a template -->
<!-- you can have as many root elements in your templates as you wish -->
<template>
<h1>{{ title }}</h1>
<!-- wrap div around your prop when you want to include conditional rendering -->
<div to=".modals" v-if="showModal">
  <!-- slots can't have a self closing tag  -->
  <Modal theme="" @close="toggleModal">
    <!-- to pass a named slot, wrap it in a template so it doesn't run in the default slot -->
    <template v-slot:links>
      <a href="#"> sign up now</a>
      <a href="#"> more info </a>
    </template>
   <h1>Ninja Giveaway!</h1> 
    <p>Grab your ninja swag for half price!</p>

   </Modal>
</div>
<div to=".modals" v-if="showModalTwo">
  <!-- slots can't have a self closing tag  -->
  <Modal @close="toggleModalTwo">
    <!-- to pass a named slot, wrap it in a template so it doesn't run in the default slot -->
   <h1> Sign up to the newsletter</h1> 
    <p>For updates and promo codes</p>
   </Modal>
</div>
<button @click="toggleModal"> open Modal </button>
<button @click="toggleModalTwo"> open Modal 2 </button>
</template>

<script>
import Modal from './components/Modal'
//The object below represents root components 
export default {
  name: 'App',
  components: { Modal },
  data() {
    return { 
      title: "My first Vue App",
      showModal: false, 
      showModalTwo: false, 
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
    }
  }
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
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>

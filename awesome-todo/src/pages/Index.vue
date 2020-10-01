<template>
  <q-page padding>
    <button
      style="position: absolute; right: 10px;"
      @click="counter++">
      {{ counter }}
    </button>

    <input
      v-model="message"
      @keyup.esc="clearMessage"
      @keyup.enter="alertMessage"
      v-autofocus
      :class="{ 'error' : message.length > 22 }"
      ref="messageInput" />

    <button @click="clearMessage">Clear</button>

    <div>{{ message.length }}</div>

    <h5
      v-if="message.length"
      class="border-grey">{{ message }}</h5>
    <h6 v-else>No Message Entered</h6>

    <hr>

    <p>Uppercase message: {{ messageUppercase }}</p>
    <p>Lowercase message: {{ message | messageLowerCase }}</p>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      message: 'I love Vue.js so much',
      counter: 0
    }
  },
  computed: {
    messageUppercase () {
      console.log('messageUppercase fired')
      return this.message.toUpperCase()
    },
    errorStyle () {
      if (this.message.length > 22) {
        return {
          color: 'red',
          background: 'pink'
        }
      }
      return null
    }
  },
  methods: {
    clearMessage () {
      this.message = ''
    },
    alertMessage () {
      alert(this.message)
    }
  },
  filters: {
    messageLowerCase (value) {
      return value.toLowerCase()
    }
  },
  directives: {
    autofocus: {
      inserted (el) {
        el.focus()
      }
    }
  },
  mounted () {
    console.log('REFS: ', this.$refs)
    this.$refs.messageInput.className = 'bg-green'
  }
}
</script>

<style>
  .border-grey {
    border: 1px solid grey;
  }
  input, button {
    font-size: 20px;
  }
  .error {
    color: red;
    background: pink;
  }
</style>

<template>
  <section id="user-goal">
    <h2>My Course Goal</h2>
    <p>{{ message1 }}</p>
    <a v-bind:href="link"><p>Some Web</p></a>
    <p v-once v-html="generateRandom()"></p>
  </section>

  <section id="events">
    <h2>Events in Action</h2>
    <button v-on:click="plusClick(5)">Add</button>
    <button v-on:click="minusClick(5)">Remove</button>
    <p>Result: {{ counter }}</p>
    <input type="text" placeholder="name" v-model="name">
    <button v-on:click="reset()">Reset</button>
    <p>Your name : {{fullname}}</p>
    <form v-on:submit.prevent="formSubmit">
      <input type="text" name="" id="" placeholder="user name">
      <button>Submit</button>
    </form>
  </section>

  <section id="styling">
      <div :class="['demo', aHoverComputed]" @click="divHover('A')"></div>
      <div :class="['demo', bHoverComputed]" @click="divHover('B')"></div>
      <div :class="['demo', cHoverComputed]" @click="divHover('C')"></div>
    </section>
</template>

<script>
export default {
  data () {
    return {
      message1: '<h1>Some Message</h1>',
      message2: 'Message 2',
      link: 'http://www.someweb.com',
      counter: 0,
      name: '',
      confirmedName: '',
      aHover: false,
      bHover: false,
      cHover: false
    }
  },
  computed: {
    fullname () {
      return this.name + '' + 'ggwp'
    },
    // eslint-disable-next-line vue/no-dupe-keys
    aHoverComputed () {
      return { active: this.aHover }
    },
    // eslint-disable-next-line vue/no-dupe-keys
    bHoverComputed () {
      return { active: this.bHover }
    },
    // eslint-disable-next-line vue/no-dupe-keys
    cHoverComputed () {
      return { active: this.cHover }
    }
  },
  methods: {
    generateRandom () {
      const random = Math.random()
      console.log(random)
      return random < 0.5 ? this.message1 : this.message2
    },
    plusClick (num) {
      this.counter += num
      return this.counter
    },
    minusClick (num) {
      this.counter -= num
      return this.counter
    },
    nameChange (event) {
      this.name = event.target.value
    },
    formSubmit (event) {
      event.preventDefault()
      alert('submit')
    },
    confirmName () {
      this.confirmedName = this.name
    },
    reset () {
      this.name = ''
    },
    divHover (div) {
      this.aHover = div === 'A'
      this.bHover = div === 'B'
      this.cHover = div === 'C'
    }
  }
}
</script>

<style lang="css" scoped>
  #user-goal {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#user-goal h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #4fc08d;
  margin: 0 0 1rem 0;
}

#user-goal p {
  font-size: 1.25rem;
  font-weight: bold;
  border: 1px solid #4fc08d;
  background-color: #4fc08d;
  color: white;
  padding: 0.5rem;
  border-radius: 25px;
}

#user-goal input {
  font: inherit;
  border: 1px solid #ccc;
}

#user-goal input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#user-goal button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#user-goal button:hover,
#user-goal button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

#events {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#events h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #4fc08d;
  margin: 0 0 1rem 0;
}

#events p {
  font-size: 1.25rem;
  font-weight: bold;
  border: 1px solid #4fc08d;
  background-color: #4fc08d;
  color: white;
  padding: 0.5rem;
  border-radius: 25px;
}

#events input {
  font: inherit;
  border: 1px solid #ccc;
}

#events input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#events button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  border-radius: 20px;
  margin: 0 1rem;
}

#events button:hover,
#events button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

#styling {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

.demo {
  width: calc(100% - 32px);
  height: 100px;
  margin: 16px;
  border: 2px dashed #ccc;
}

.active {
  background-color: salmon;
  border-color: red;
}

</style>

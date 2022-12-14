<template>
  <section class="main-content">
    <!-- Add itemm, and prioritize -->
    <form @submit.prevent="saveItem" class="add-item-form">
      <!-- Binds user input -->
      <input v-model.trim="newItem" type="text" placeholder="Add item">
      <label for="priority" value="High Priority">
        High Priority
        <input type="checkbox" v-model="newItemHighPriority">
      </label>
      <!-- save button -->
      <!-- <button :disabled="newItem.length < 3" class="btn btn-primary" :class="{ disabled: newItem.length < 3 }">Save Item</button> -->
      <button
        :disabled="newItem.length < 3"
        :class="[ newItem.length < 3 ? 'disabled' : 'btn' ]"
        >Save Item
      </button>
    </form>
    <!-- Start of the shopping list -->
    <ul>
      <li @click="toggleDone(item)" v-for="item in filteredItems" :key="item.id">
        <span class="list-item" :class="{ done: item.done, priority: item.highPriority }">{{ item.label }}</span>
        <button class="close" @click="removeItem(item)">Remove</button>
      </li>
    </ul>
    <p v-if="items.length === 0">Nothing on the list 😞</p>
    <button class="btn-done" @click="hideCompleted = !hideCompleted">
      {{ hideCompleted ? 'Show all' : 'Hide completed' }}
    </button>
  </section>
</template>

<script>
// set id to a value to start
let id = 0

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      header: '',
      newItem: '', // create empty array to start the item
      newItemHighPriority: false, // sets the priority to off initially
      hideCompleted: false,
      editing: false,
      items: [
        { id: id++, label: 'carrots', done: true, highPriority: false },
        { id: id++, label: 'apples', done: true, highPriority: false },
        { id: id++, label: 'oranges', done: false, highPriority: true }
      ]
    }
  },
  computed: {
    reversedItems () {
      return [...this.items].reverse()
    },
    filteredItems () {
      return this.hideCompleted ? this.items.filter((t) => !t.done) : this.items
    }
  },
  methods: {
    saveItem () {
      this.items.push({ id: id++, label: this.newItem, done: false, highPriority: this.newItemHighPriority }) // adding a new item with a new id by pushing on to the array
      this.newItem = '' // clears out the form
      this.newItemHighPriority = ''
    },
    removeItem (item) {
      this.items = this.items.filter((t) => t !== item)
    },
    toggleDone (item) {
      item.done = !item.done
    },
    toggle () {
      this.editing = !this.editing
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.add-item-form .disabled {
  cursor: not-allowed;
  background-color: rgb(203 213 225);
  font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing:antialiased; -moz-osx-font-smoothing: grayscale;
font-size: .75rem; border: none;
border-radius: 3px; color: #fff; font-weight: 700; display: inline-block;
padding: .75rem 1rem; transition: .2s all ease-out;
}
.main-content {
  padding: 1.75rem 1.25rem;
}
.priority {
  color: rgb(22 163 74);
  font-weight: 700;
}
.done {
  cursor: pointer;
  text-decoration: line-through;
}
form {
  display: flex;
  flex-direction: column;
  margin-bottom: 2.5rem;
}
button.close {
  display: inline-block;
  vertical-align: middle;
  background-color: rgb(239 68 68);
  color: #fff;
  border: none;
  border-radius: 3px;
  padding: .35rem .45rem;
  font-size: .75rem;
}
.btn-secondary {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 1rem;
  background-color: rgb(29 78 216);
  border: none;
  border-radius: 3px; color: #fff;
  font-weight: 700;
  display: inline-block;
  margin-bottom: 1.875rem;
  padding: .75rem 1rem;
}
.add-item-form .btn {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: .75rem;
  background-color: rgb(79 70 229);
  border: none;
  border-radius: 3px;
  color: #fff;
  font-weight: 700;
  display: inline-block;
  padding: .75rem 1rem;
  transition: .2s all ease-out;
}
.add-item-form .btn:hover {
  opacity: .8;
  cursor: pointer;
}
.btn-done {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: .75rem;
  background-color: rgb(56 189 248);
  border: none;
  border-radius: 3px;
  color: #fff;
  font-weight: 700;
  display: inline-block;
  padding: .75rem 1rem;
  transition: .2s all ease-out;
}
.add-item-form label { margin-bottom: 1.25rem; font-size: .75rem;}

.add-item-form input[type=text] {
  border: none;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  padding: .75rem;
  font-size: 1rem;
  margin-bottom: 1.25rem;
}
.add-item-form input[type=text]::placeholder {
  font-size: 1rem;
  color: rgb(148 163 184);
}
.add-item-form input[type=checkbox] {
  vertical-align: middle;
}
h1 {
  font-weight: 700;
  font-size: 3rem;
  letter-spacing: -.75px;
  line-height: 1.2;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: flex;
  justify-content: space-between;
  cursor: pointer;
  font-size: 1.25rem;
  margin-bottom: 1.25rem;
}
li span {
  display: inline-block;
}
li span:hover {
  box-shadow: rgba(0, 0, 0, 0.1) 0px 10px 15px -3px, rgba(0, 0, 0, 0.05) 0px 4px 6px -2px;
}
a {
  color: #42b983;
}
ul {
  display: flex;
  flex-direction: column;
  margin-bottom: 2.5em;
}
p {
  font-size: 1.5rem;
  font-weight: 700;
}

</style>

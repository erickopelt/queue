<template>
  <div class="hello">
    <div class="enqueue">
      <input type="number" v-model="enqueueValue" name="" value="" class="queue-input form-input">
      <br>
      <button type="button"
      v-on:click="enqueue(enqueueValue)" class="btn">Enqueue</button>
    </div>
    <div class="dequeue">
      <button type="button" v-on:click="dequeue()" name="button" class="btn">Dequeue</button>
    </div>
    <ul class="queue">
      <transition-group
        enter-active-class="fadeInRight"
        leave-active-class="fadeOutLeft"
        tag="ul">
        <li v-for="item in queue" v-bind:key="item.id" class="queue-item">
          <span class="item-number">{{item.value}}</span>
        </li>
      </transition-group>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      queue: [],
      enqueueValue: 0
    }
  },
  methods: {
    enqueue: function (value) {
      return this.queue.push({
        value: value,
        id: Math.random()
      })
    },
    dequeue: function () {
      return this.queue.shift()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

.queue-input{
  width: 80px;
  height: 80px;
  margin: 10px;
  padding: 10px;
}

.dequeue {
  margin-top: 10px;
}

.queue-item {
  width: 40px;
  height: 40px;
  border: 1px solid grey;
  position: relative;
}

.item-number {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.queue {
  margin: 30px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

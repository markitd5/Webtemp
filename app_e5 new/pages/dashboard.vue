<template>
    <div>
      <div>Index.vue</div>
      <h1 :title="id">{{ msg }}</h1>
      <div>{{ name.toUpperCase() + sw }}</div>
      <div><h1>{{ status }}</h1></div>
      <div>
      <v-btn
        class="ma-2"
        color="primary"
      >
        {{ status}}
        <v-icon
          icon="mdi-checkbox-marked-circle"
          end
        ></v-icon>
      </v-btn>
      </div>
      <input v-model="id" type="text">
      <button @click="add">CLICK</button>
    </div>

    <template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="auto">
        <v-btn density="compact" icon="mdi-plus"></v-btn>
      </v-col>

      <v-col cols="auto">
        <v-btn density="comfortable" icon="$vuetify"></v-btn>
      </v-col>

      <v-col cols="auto">
        <v-btn density="default" icon="mdi-open-in-new"></v-btn>
      </v-col>
    </v-row>

    <v-row align="center" justify="center">
      <v-col cols="auto">
        <v-btn icon="mdi-account" size="x-small"></v-btn>
      </v-col>

      <v-col cols="auto">
        <v-btn icon="mdi-plus" size="small"></v-btn>
      </v-col>

      <v-col cols="auto">
        <v-btn icon="$vuetify"></v-btn>
      </v-col>

      <v-col cols="auto">
        <v-btn icon="mdi-open-in-new" size="large"></v-btn>
      </v-col>

      <v-col cols="auto">
        <v-btn icon="mdi-calendar" size="x-large"></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>
  </template>
  <script>
  //   const mqtt = require('mqtt')
  import mqtt from "mqtt";
  definePageMeta({
  layout: "custom",
  });
  export default {
    data() {
      return {
        id: 10,
        name: 'hello',
        msg: '',
        sw: '',
        status: ''
      }
    }, // data
  
    created() {
      this.client = mqtt.connect('ws://broker.emqx.io:8083/mqtt')
      this.client.on('connect', this.onMqttConnect.bind(this))
      this.client.on('message', this.onMqttMessage.bind(this))
    }, // created
  
    beforeDestroy() {
      // if (this.client) {
      //   this.client.end()
      // }
      this.client && this.client.end()
    }, // beforeDestroy
  
    methods: {
      add() {
        let sw = this.id++
        this.client.publish('op-001', String(sw))
      }, // add
  
      onMqttConnect() {
        console.log('connected')
        this.status = 'Mqtt  connected'
        this.client.publish('op', 'status')
        this.client.subscribe('status', err => err)
        this.client.subscribe('room1', err => err)
      }, // onMqttConnect
  
      onMqttMessage(topic, message) {
        if (topic === 'status') {
          // message is Buffer
          console.log('GOT:', message.toString())
          this.msg = message.toString()
        }
        if(topic === 'room1'){
          console.log('lamp 1 On')
        }
      }, // onMqttMessage
    }, // methods
  }
  </script>
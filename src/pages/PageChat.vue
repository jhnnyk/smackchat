<template>
  <q-page class="flex column">
    <q-banner class="bg-grey-4 text-center"> User is offline. </q-banner>

    <div class="q-pa-md column col justify-end">
      <div class="row justify-center">
        <div style="width: 100%; max-width: 400px">
          <q-chat-message
            v-for="message in messages"
            :key="message.text"
            :name="message.from"
            :text="[message.text]"
            :sent="message.from == 'me' ? true : false"
          />
        </div>
      </div>
    </div>

    <q-footer elevated>
      <q-toolbar>
        <q-form @submit="sendMessage" class="full-width">
          <div class="row">
            <q-input
              bg-color="white"
              class="col-11"
              rounded
              outlined
              v-model="newMessage"
              label="Message"
              dense
            >
            </q-input>

            <q-btn
              color="white"
              class="col-1"
              round
              dense
              flat
              icon="send"
              type="submit"
            />
          </div>
        </q-form>
      </q-toolbar>
    </q-footer>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const newMessage = ref('')
const messages = ref([
  {
    text: 'Hey how are you?',
    from: 'me',
  },
  {
    text: 'good thanks! how are you?',
    from: 'them',
  },
  {
    text: 'Pretty good',
    from: 'me',
  },
  {
    text: 'Really?',
    from: 'them',
  },
])

const sendMessage = () => {
  messages.value.push({
    text: newMessage.value,
    from: 'me',
  })
}
</script>

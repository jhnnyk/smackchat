<template>
  <q-form @submit="submitForm">
    <q-input
      v-if="tab == 'register'"
      class="q-mb-md"
      outlined
      v-model="formData.name"
      label="Name"
    />
    <q-input
      class="q-mb-md"
      outlined
      v-model="formData.email"
      label="Email"
      type="email"
    />
    <q-input
      class="q-mb-md"
      outlined
      v-model="formData.password"
      label="Password"
      type="password"
    />
    <div class="row">
      <q-space />
      <q-btn color="primary" :label="tab" type="submit" />
    </div>
  </q-form>
</template>

<script setup>
import { reactive } from 'vue'
import { useStore } from 'src/stores/store'

const props = defineProps({ tab: String })
const store = useStore()

const formData = reactive({
  name: '',
  email: '',
  password: '',
})

const submitForm = () => {
  if (props.tab == 'login') {
    console.log('login the user')
  } else {
    store.registerUser(formData)
  }
}
</script>

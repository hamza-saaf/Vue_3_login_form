<template>
  <form @submit.prevent="handleSubmit" class="bg-white p-8 rounded-lg shadow-md w-full max-w-sm">
    <h2 class="login-title text-xl font-semibold mb-4">Login</h2>

    <div class="mb-4">
      <label for="email" class="block mb-1">Email : </label>
      <input
        type="email"
        id="email"
        v-model="email"
        class="border px-3 py-2 rounded w-full"
        :class="{ 'border-red-500': errors.email }"
      />
      <p v-if="errors.email" class="text-red-500 text-sm">{{ errors.email }}</p>
    </div>

    <div class="mb-4">
      <label for="password" class="block mb-1">Password : </label>
      <input
        type="password"
        id="password"
        v-model="password"
        class="border px-3 py-2 rounded w-full"
        :class="{ 'border-red-500': errors.password }"
      />
      <p v-if="errors.password" class="text-red-500 text-sm">{{ errors.password }}</p>
    </div>

    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600">
      Login
    </button>
  </form>
</template>

<script setup>
import { ref, reactive } from 'vue'

const email = ref('')
const password = ref('')
const errors = reactive({
  email: '',
  password: ''
})

function handleSubmit() {
  errors.email = ''
  errors.password = ''

  if (!email.value.includes('@')) {
    errors.email = 'Please enter a valid email address'
  }

  if (password.value.length < 6) {
    errors.password = 'Password must be at least 6 characters.'
  }

  if (!errors.email && !errors.password) {
    alert('Login successful!')
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 100%;
  max-width: 400px;
  padding: 2rem;
  border-radius: 12px;
  background-color: #ffffff;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1);
  margin: 0 auto;
}
.login-title {
  text-align: center;
}
:global(body) {
  margin: 0;
  padding: 0;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(145deg, #f0f4f8, #e2e8f0);
  font-family: 'Segoe UI', sans-serif;
}

label {
  font-weight: 600;
  margin-bottom: 0.25rem;
}

input {
  padding: 0.6rem 0.8rem;
  border-radius: 8px;
  border: 1px solid #ccc;
  transition: border 0.3s ease;
  font-size: 1rem;
  width: 100%;
}

input:hover{
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 2px rgba(59, 130, 246, 0.2);
}

p {
  margin: 0;
  font-size: 0.875rem;
  color: #dc2626;
}


button {
  padding: 0.6rem;
  background-color: #090a0b;
  color: white;
  font-weight: 600;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background 0.3s ease;
}

button:hover {
  background-color: #818792;
}


</style>

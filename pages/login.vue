<template>
  <div class="min-h-screen bg-[#F8F9FA] flex flex-col justify-center py-8 md:py-12 px-4 sm:px-6 lg:px-8 relative overflow-hidden">
    
    <div class="absolute -top-40 -right-40 w-72 h-72 md:w-96 md:h-96 bg-blue-100 rounded-full mix-blend-multiply filter blur-3xl opacity-50"></div>
    <div class="absolute -bottom-40 -left-40 w-72 h-72 md:w-96 md:h-96 bg-indigo-100 rounded-full mix-blend-multiply filter blur-3xl opacity-50"></div>

    <div class="sm:mx-auto sm:w-full sm:max-w-md relative z-10">
      <div class="w-14 h-14 md:w-16 md:h-16 bg-gradient-to-br from-blue-600 to-indigo-700 rounded-2xl text-white flex items-center justify-center mx-auto mb-4 md:mb-6 shadow-lg shadow-blue-500/30 border border-blue-400">
        <span class="material-symbols-outlined text-3xl md:text-4xl">inventory_2</span>
      </div>
      
      <h2 class="text-center text-2xl md:text-3xl font-extrabold text-gray-900 tracking-tight">
        Masuk ke WMS <span class="text-blue-600">3PL</span>
      </h2>
      <p class="mt-1 md:mt-2 text-center text-xs md:text-sm text-gray-500 font-medium">
        Sistem Manajemen Gudang Terpusat
      </p>
    </div>

    <div class="mt-6 md:mt-8 sm:mx-auto w-full sm:max-w-md relative z-10">
      <div class="bg-white py-6 px-5 md:py-8 md:px-10 shadow-xl shadow-gray-200/50 rounded-2xl md:rounded-3xl border border-gray-100">
        <form class="space-y-4 md:space-y-5" @submit.prevent="handleLogin">
          <div>
            <label for="username" class="block text-[10px] md:text-xs font-bold text-gray-600 uppercase tracking-wider mb-1.5 md:mb-2">Username</label>
            <div class="relative">
              <span class="material-symbols-outlined absolute left-4 top-1/2 transform -translate-y-1/2 text-gray-400 text-base md:text-lg">person</span>
              <input 
                id="username" 
                v-model="username" 
                type="text" 
                required 
                placeholder="Masukkan username Anda"
                class="appearance-none block w-full pl-10 md:pl-11 pr-4 py-2.5 md:py-3 border border-gray-200 rounded-xl text-gray-900 bg-gray-50 hover:bg-white focus:bg-white focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors text-sm font-medium"
              >
            </div>
          </div>

          <div>
            <label for="password" class="block text-[10px] md:text-xs font-bold text-gray-600 uppercase tracking-wider mb-1.5 md:mb-2">Password</label>
            <div class="relative">
              <span class="material-symbols-outlined absolute left-4 top-1/2 transform -translate-y-1/2 text-gray-400 text-base md:text-lg">lock</span>
              <input 
                id="password" 
                v-model="password" 
                type="password" 
                required 
                placeholder="••••••••"
                class="appearance-none block w-full pl-10 md:pl-11 pr-4 py-2.5 md:py-3 border border-gray-200 rounded-xl text-gray-900 bg-gray-50 hover:bg-white focus:bg-white focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-blue-500 transition-colors text-sm font-medium"
              >
            </div>
          </div>

          <div v-if="errorMessage" class="text-xs md:text-sm text-red-600 bg-red-50 p-2.5 md:p-3 rounded-xl border border-red-100 text-center font-semibold flex items-center justify-center">
            <span class="material-symbols-outlined text-[16px] md:text-[18px] mr-1">error</span>
            {{ errorMessage }}
          </div>

          <div class="pt-2 md:pt-2">
            <button type="submit" class="w-full flex justify-center py-2.5 md:py-3 px-4 border border-transparent rounded-xl shadow-md shadow-blue-500/20 text-sm font-bold text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 transition-all active:scale-[0.98]">
              Sign in ke Sistem
            </button>
          </div>
        </form>

        <div class="mt-6 md:mt-8 bg-blue-50/50 border border-blue-100 rounded-2xl p-4 md:p-5">
          <div class="flex items-center mb-2.5 md:mb-3 text-blue-800">
            <span class="material-symbols-outlined text-base md:text-lg mr-1.5 md:mr-2">info</span>
            <h3 class="text-[10px] md:text-xs uppercase font-bold tracking-wider">Kredensial Presentasi</h3>
          </div>
          <ul class="text-xs md:text-sm text-gray-600 space-y-2 md:space-y-2.5">
            <li class="flex flex-col sm:flex-row sm:justify-between sm:items-center bg-white px-3 py-2 rounded-lg border border-gray-100 shadow-sm gap-1 sm:gap-0">
              <span class="font-medium text-gray-500 text-[10px] md:text-xs">Super Admin</span>
              <span class="font-mono font-bold text-gray-800 text-xs">admin <span class="text-gray-300 mx-1">|</span> pass123</span>
            </li>
            <li class="flex flex-col sm:flex-row sm:justify-between sm:items-center bg-white px-3 py-2 rounded-lg border border-gray-100 shadow-sm gap-1 sm:gap-0">
              <span class="font-medium text-gray-500 text-[10px] md:text-xs">Client 1 (CA Skin)</span>
              <span class="font-mono font-bold text-gray-800 text-xs">caskin <span class="text-gray-300 mx-1">|</span> pass123</span>
            </li>
            <li class="flex flex-col sm:flex-row sm:justify-between sm:items-center bg-white px-3 py-2 rounded-lg border border-gray-100 shadow-sm gap-1 sm:gap-0">
              <span class="font-medium text-gray-500 text-[10px] md:text-xs">Client 2 (Packaging)</span>
              <span class="font-mono font-bold text-gray-800 text-xs">packaging <span class="text-gray-300 mx-1">|</span> pass123</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

definePageMeta({ layout: false })

const username = ref('')
const password = ref('')
const errorMessage = ref('')
const currentUser = useState('user', () => null)

const mockUsers = [
  { username: 'admin', password: 'pass123', name: 'Bapak Royan', role: 'super_admin', assigned_brand: 'All' },
  { username: 'caskin', password: 'pass123', name: 'Admin CA Skin', role: 'brand_client', assigned_brand: 'CA SKIN GLOW' },
  { username: 'packaging', password: 'pass123', name: 'Admin Packaging', role: 'brand_client', assigned_brand: 'Packaging Packing' }
]

const handleLogin = () => {
  const user = mockUsers.find(u => u.username === username.value && u.password === password.value)
  if (user) {
    currentUser.value = user
    errorMessage.value = ''
    navigateTo('/')
  } else {
    errorMessage.value = 'Username atau password salah!'
  }
}
</script>
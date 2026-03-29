<template>
  <div class="pb-10 max-w-7xl mx-auto">
    
    <nav class="flex items-center text-[11px] md:text-sm font-medium text-gray-500 mb-4 md:mb-6 overflow-x-auto whitespace-nowrap pb-2 scrollbar-hide">
      <NuxtLink to="/" class="hover:text-blue-600 flex items-center transition-colors group">
        <span class="material-symbols-outlined text-[16px] md:text-[18px] mr-1 md:mr-1.5 group-hover:text-blue-600 transition-colors">home</span>
        Dashboard
      </NuxtLink>
      <span class="material-symbols-outlined text-[14px] md:text-[18px] text-gray-400 mx-1 md:mx-1.5">chevron_right</span>
      <NuxtLink to="/outbound" class="hover:text-blue-600 transition-colors">
        Outbound
      </NuxtLink>
      <span class="material-symbols-outlined text-[14px] md:text-[18px] text-gray-400 mx-1 md:mx-1.5">chevron_right</span>
      <span class="text-blue-700 font-bold bg-blue-50 px-2 py-0.5 md:px-2.5 md:py-1 rounded-md border border-blue-100 shadow-sm">
        Riwayat Lengkap
      </span>
    </nav>
    
    <div class="mb-6 md:mb-8 flex flex-col sm:flex-row sm:items-center justify-between gap-4">
      <div class="flex items-center">
        <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl bg-orange-50 text-orange-600 flex items-center justify-center mr-3 md:mr-4 shrink-0 shadow-sm border border-orange-100">
          <span class="material-symbols-outlined text-xl md:text-2xl">receipt_long</span>
        </div>
        <div>
          <h2 class="text-xl md:text-2xl lg:text-3xl font-bold text-gray-900 leading-tight">Riwayat Lengkap Outbound</h2>
          <p class="text-xs md:text-sm text-gray-500 mt-0.5 md:mt-1">Semua data pemindaian resi dan pengeluaran stok.</p>
        </div>
      </div>
      
      <NuxtLink to="/outbound" class="w-full sm:w-auto inline-flex items-center justify-center px-4 py-2.5 md:py-2.5 bg-white border border-gray-200 rounded-xl text-sm font-semibold text-gray-700 hover:bg-gray-50 transition-colors shadow-sm">
        <span class="material-symbols-outlined text-[16px] md:text-[18px] mr-2">arrow_back</span>
        Kembali ke Outbound
      </NuxtLink>
    </div>
    
    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 p-4 md:p-6 mb-6 md:mb-8">
      <div class="relative w-full">
        <span class="material-symbols-outlined absolute left-3 md:left-4 top-1/2 transform -translate-y-1/2 text-gray-400 text-lg md:text-xl">search</span>
        <input 
          v-model="searchQuery" 
          type="text" 
          placeholder="Cari No. Resi, SKU, Ekspedisi, atau Platform..." 
          class="w-full pl-10 md:pl-12 pr-4 py-2.5 md:py-3 border border-gray-200 rounded-xl text-sm focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none transition-colors bg-gray-50 hover:bg-white text-gray-800 font-medium"
        >
      </div>
    </div>

    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden">
      <div class="overflow-x-auto w-full pb-2">
        <table class="w-full text-left min-w-[850px] md:min-w-[950px]">
          <thead class="bg-white text-gray-500 text-[10px] md:text-[11px] uppercase tracking-wider md:tracking-widest border-b border-gray-100">
            <tr>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold whitespace-nowrap">Tanggal & Waktu</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold whitespace-nowrap">No. Resi (Waybill)</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold whitespace-nowrap">Brand</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold whitespace-nowrap">Platform & Ekspedisi</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold whitespace-nowrap">SKU Keluar</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold text-center whitespace-nowrap">Status</th>
            </tr>
          </thead>
          <tbody class="text-xs md:text-sm divide-y divide-gray-50">
            <tr v-for="(item, index) in filteredHistory" :key="index" class="hover:bg-blue-50/30 transition-colors group">
              <td class="px-4 py-3 md:px-6 md:py-4 whitespace-nowrap">
                <div class="font-bold text-gray-800 text-xs md:text-sm">{{ item.date }}</div>
                <div class="text-[10px] md:text-xs text-gray-500 font-medium mt-0.5">{{ item.time }}</div>
              </td>
              
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono font-bold text-gray-900 text-[11px] md:text-sm md:tracking-wide">
                {{ item.receipt }}
              </td>
              
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="font-medium text-gray-800 bg-gray-100 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[9px] md:text-[11px] border border-gray-200">
                  {{ item.brand }}
                </span>
              </td>
              
              <td class="px-4 py-3 md:px-6 md:py-4 flex items-center gap-2">
                <span :class="getPlatformClass(item.platform)">
                  {{ item.platform }}
                </span>
                <span class="font-bold text-gray-500 text-[10px] md:text-xs">via</span>
                <span :class="getExpeditionClass(item.ekspedisi)">
                  {{ item.ekspedisi }}
                </span>
              </td>
              
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono text-gray-700 font-medium text-[11px] md:text-sm">
                <div class="flex items-center">
                  {{ item.sku }} 
                  <span class="text-white font-bold ml-1.5 md:ml-2 bg-red-500 px-1.5 py-0.5 rounded text-[9px] md:text-[10px] shadow-sm">
                    -{{ item.qty }}
                  </span>
                </div>
              </td>
              
              <td class="px-4 py-3 md:px-6 md:py-4">
                <div class="flex justify-center">
                  <span v-if="item.status === 'Sukses'" class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[110px] border border-green-200 shadow-sm">
                    <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1 md:mr-1.5">check_circle</span> Sukses
                  </span>
                  <span v-else class="inline-flex items-center justify-center bg-red-50 text-red-700 px-2 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[110px] border border-red-200 shadow-sm">
                    <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1 md:mr-1.5">cancel</span> Gagal
                  </span>
                </div>
              </td>
            </tr>

            <tr v-if="filteredHistory.length === 0">
              <td colspan="6" class="px-4 py-12 md:px-6 md:py-16 text-center text-gray-400">
                <span class="material-symbols-outlined text-4xl md:text-5xl block mb-2 md:mb-3 opacity-20">search_off</span>
                <span class="font-medium text-sm">Tidak ada riwayat outbound yang sesuai.</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      
      <div class="px-4 py-3 md:px-6 md:py-4 border-t border-gray-100 bg-gray-50/30 flex flex-col sm:flex-row justify-between items-center gap-3 md:gap-4 text-xs md:text-sm text-gray-500">
        <span class="font-medium">Menampilkan {{ filteredHistory.length }} data</span>
        <div class="flex gap-2 w-full sm:w-auto justify-center">
          <button class="flex-1 sm:flex-none px-3 py-1.5 border border-gray-200 rounded-lg hover:bg-gray-50 disabled:opacity-50 font-medium transition-colors" disabled>Prev</button>
          <button class="px-3 py-1.5 bg-blue-600 text-white rounded-lg font-bold shadow-sm">1</button>
          <button class="px-3 py-1.5 border border-gray-200 rounded-lg hover:bg-gray-50 disabled:opacity-50 font-medium transition-colors" disabled>Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

// 1. Cek User Akses
const currentUser = useState('user')
if (!currentUser.value) {
  navigateTo('/login')
}

const searchQuery = ref('')
const globalSelectedBrand = useState('selectedBrand')

// 2. Dummy Data Riwayat Outbound
const allOutboundHistory = [
  { date: '27 Mar 2026', time: '14:20 WIB', receipt: 'JP8819203910', brand: 'CA SKIN GLOW', ekspedisi: 'J&T', platform: 'Shopee', sku: 'CAS001', qty: 1, status: 'Sukses' },
  { date: '27 Mar 2026', time: '13:15 WIB', receipt: 'JX9901823111', brand: 'CA SKIN GLOW', ekspedisi: 'J&T', platform: 'TikTok', sku: 'CAM001', qty: 2, status: 'Sukses' },
  { date: '27 Mar 2026', time: '11:05 WIB', receipt: 'TK112938884', brand: 'Brand X', ekspedisi: 'JNE', platform: 'Tokopedia', sku: 'BRX-001', qty: 1, status: 'Sukses' },
  { date: '26 Mar 2026', time: '16:45 WIB', receipt: '0012938812', brand: 'Packaging Packing', ekspedisi: 'Sicepat', platform: 'Mengantar', sku: 'POLY01', qty: 5, status: 'Sukses' },
  { date: '26 Mar 2026', time: '10:10 WIB', receipt: 'LX001928374', brand: 'CA SKIN GLOW', ekspedisi: 'LEX ID', platform: 'Lazada', sku: 'CASM001', qty: 1, status: 'Sukses' },
  { date: '25 Mar 2026', time: '09:30 WIB', receipt: 'JP9988776655', brand: 'Brand X', ekspedisi: 'J&T', platform: 'Shopee', sku: 'BRX-002', qty: 3, status: 'Sukses' },
]

// 3. Logika Filter Terintegrasi
const filteredHistory = computed(() => {
  if (!currentUser.value) return []

  let result = allOutboundHistory

  // Filter berdasarkan Role Akses atau Global Filter Atas
  if (currentUser.value.role !== 'super_admin') {
    result = result.filter(item => item.brand === currentUser.value.assigned_brand)
  } else {
    if (globalSelectedBrand.value && globalSelectedBrand.value !== 'Semua Brand') {
      result = result.filter(item => item.brand === globalSelectedBrand.value)
    }
  }

  // Filter berdasarkan Teks Pencarian
  if (searchQuery.value) {
    const query = searchQuery.value.toLowerCase()
    result = result.filter(item => 
      item.receipt.toLowerCase().includes(query) || 
      item.sku.toLowerCase().includes(query) ||
      item.ekspedisi.toLowerCase().includes(query) ||
      item.platform.toLowerCase().includes(query)
    )
  }

  return result
})

// 4. Fungsi Styling Dinamis untuk Badge
const getPlatformClass = (platform) => {
  const baseClass = 'px-2.5 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold shadow-sm '
  if (platform.toLowerCase() === 'shopee') return baseClass + 'bg-[#ffede5] text-[#ee4d2d] border border-[#ffcdb8]'
  if (platform.toLowerCase() === 'tiktok') return baseClass + 'bg-gray-900 text-white border border-gray-700'
  if (platform.toLowerCase() === 'tokopedia') return baseClass + 'bg-green-50 text-green-700 border border-green-200'
  if (platform.toLowerCase() === 'lazada') return baseClass + 'bg-blue-50 text-blue-700 border border-blue-200'
  // Default (Mengantar, dll)
  return baseClass + 'bg-purple-50 text-purple-700 border border-purple-200'
}

const getExpeditionClass = (ekspedisi) => {
  const baseClass = 'px-2 py-1 md:px-2.5 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold border '
  if (ekspedisi.includes('J&T') || ekspedisi.includes('Sicepat')) return baseClass + 'bg-red-50 text-red-600 border-red-100'
  if (ekspedisi.includes('JNE') || ekspedisi.includes('LEX')) return baseClass + 'bg-blue-50 text-blue-600 border-blue-100'
  // Default
  return baseClass + 'bg-gray-50 text-gray-700 border-gray-200'
}
</script>
<template>
  <div class="pb-6 md:pb-10 max-w-7xl mx-auto">
    <div class="mb-6 md:mb-8">
      <h2 class="text-xl md:text-3xl font-bold text-gray-900">Dashboard Stok</h2>
      <p class="text-xs md:text-sm text-gray-500 mt-1">Pantau ketersediaan barang dan pergerakan stok secara real-time.</p>
    </div>
    
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 md:gap-5 mb-6 md:mb-8">
      
      <div class="bg-white rounded-2xl p-5 md:p-6 shadow-sm border border-gray-100 hover:shadow-md transition-shadow">
        <div class="flex justify-between items-start">
          <div>
            <p class="text-xs md:text-sm font-medium text-gray-500 mb-1">Total Stok Tersedia</p>
            <h3 class="text-2xl md:text-3xl font-bold text-gray-900">{{ totalStok.toLocaleString('id-ID') }}</h3>
          </div>
          <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl bg-blue-50 flex items-center justify-center text-blue-600 shrink-0">
            <span class="material-symbols-outlined text-xl md:text-2xl">inventory_2</span>
          </div>
        </div>
        <div class="mt-3 md:mt-4 text-[11px] md:text-xs font-medium text-gray-400 flex items-center">
          <span class="text-blue-500 bg-blue-50 px-2 py-0.5 rounded text-[10px] mr-2">Pcs</span> Semua gudang
        </div>
      </div>
      
      <div class="bg-white rounded-2xl p-5 md:p-6 shadow-sm border border-gray-100 hover:shadow-md transition-shadow">
        <div class="flex justify-between items-start">
          <div>
            <p class="text-xs md:text-sm font-medium text-gray-500 mb-1">Inbound Bulan Ini</p>
            <h3 class="text-2xl md:text-3xl font-bold text-gray-900">{{ totalInbound.toLocaleString('id-ID') }}</h3>
          </div>
          <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl bg-green-50 flex items-center justify-center text-green-600 shrink-0">
            <span class="material-symbols-outlined text-xl md:text-2xl">local_shipping</span>
          </div>
        </div>
        <div class="mt-3 md:mt-4 text-[11px] md:text-xs font-medium text-gray-400 flex items-center">
          <span class="text-green-500 bg-green-50 px-2 py-0.5 rounded text-[10px] mr-2">Pcs</span> Total masuk
        </div>
      </div>
      
      <div class="bg-white rounded-2xl p-5 md:p-6 shadow-sm border border-gray-100 hover:shadow-md transition-shadow">
        <div class="flex justify-between items-start">
          <div>
            <p class="text-xs md:text-sm font-medium text-gray-500 mb-1">Total SKU Aktif</p>
            <h3 class="text-2xl md:text-3xl font-bold text-gray-900">{{ filteredProducts.length }}</h3>
          </div>
          <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl bg-purple-50 flex items-center justify-center text-purple-600 shrink-0">
            <span class="material-symbols-outlined text-xl md:text-2xl">category</span>
          </div>
        </div>
        <div class="mt-3 md:mt-4 text-[11px] md:text-xs font-medium text-gray-400 flex items-center">
          <span class="text-purple-500 bg-purple-50 px-2 py-0.5 rounded text-[10px] mr-2">Item</span> Tipe produk
        </div>
      </div>
      
      <div class="bg-white rounded-2xl p-5 md:p-6 shadow-sm border border-gray-100 hover:shadow-md transition-shadow">
        <div class="flex justify-between items-start">
          <div>
            <p class="text-xs md:text-sm font-medium text-gray-500 mb-1">Peringatan Stok</p>
            <h3 class="text-2xl md:text-3xl font-bold" :class="lowStockCount > 0 ? 'text-red-600' : 'text-gray-900'">{{ lowStockCount }}</h3>
          </div>
          <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl flex items-center justify-center shrink-0" :class="lowStockCount > 0 ? 'bg-red-50 text-red-600' : 'bg-gray-50 text-gray-400'">
            <span class="material-symbols-outlined text-xl md:text-2xl">warning</span>
          </div>
        </div>
        <div class="mt-3 md:mt-4 text-[11px] md:text-xs font-medium text-gray-400 flex items-center">
          <span v-if="lowStockCount > 0" class="text-red-500 bg-red-50 px-2 py-0.5 rounded text-[10px] mr-2">SKU</span> 
          <span v-else class="text-gray-500 bg-gray-100 px-2 py-0.5 rounded text-[10px] mr-2">SKU</span> 
          Butuh restock segera
        </div>
      </div>
    </div>

    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden">
      <div class="px-4 py-4 md:px-6 md:py-5 border-b border-gray-100 flex flex-col sm:flex-row sm:justify-between sm:items-center gap-3">
        <div class="flex items-center">
          <div class="w-7 h-7 md:w-8 md:h-8 rounded-lg bg-blue-50 text-blue-600 flex items-center justify-center mr-3">
            <span class="material-symbols-outlined text-xs md:text-sm">list_alt</span>
          </div>
          <h3 class="font-bold text-gray-900 text-base md:text-lg">Rincian Inventori</h3>
        </div>
        <span class="text-[10px] md:text-xs bg-green-50 text-green-700 py-1 px-2.5 md:py-1.5 md:px-3 rounded-md font-semibold flex items-center border border-green-100 w-fit">
          <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1">sync</span> Data terupdate
        </span>
      </div>
      
      <div class="overflow-x-auto w-full pb-2">
        <table class="w-full text-left min-w-[650px]">
          <thead class="bg-gray-50/50 text-gray-500 text-[10px] md:text-xs uppercase tracking-wider">
            <tr>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">Brand</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">SKU</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">Nama Produk</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold text-right whitespace-nowrap">Sisa Stok</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold text-center whitespace-nowrap">Status</th>
            </tr>
          </thead>
          <tbody class="text-xs md:text-sm divide-y divide-gray-100">
            <tr v-for="item in filteredProducts" :key="item.sku" class="hover:bg-gray-50/80 transition-colors">
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="font-medium text-gray-800 bg-gray-100 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs border border-gray-200 whitespace-nowrap">{{ item.brand }}</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono text-gray-500 text-[11px] md:text-xs">{{ item.sku }}</td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-medium text-gray-700 min-w-[180px]">{{ item.name }}</td>
              <td class="px-4 py-3 md:px-6 md:py-4 text-right">
                <span class="font-bold text-sm md:text-base" :class="item.stock < 50 ? 'text-red-600' : 'text-gray-900'">
                  {{ item.stock.toLocaleString('id-ID') }}
                </span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 flex justify-center">
                <span v-if="item.stock < 50" class="inline-flex items-center justify-center bg-red-50 text-red-700 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[100px] border border-red-100">
                  <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1">error</span> Kritis
                </span>
                <span v-else class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[100px] border border-green-100">
                  <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1">check_circle</span> Aman
                </span>
              </td>
            </tr>
            
            <tr v-if="filteredProducts.length === 0">
              <td colspan="5" class="px-4 py-12 md:px-6 md:py-16 text-center text-gray-400">
                <span class="material-symbols-outlined text-4xl md:text-5xl block mb-2 md:mb-3 opacity-20">inventory_2</span>
                <span class="font-medium text-sm">Tidak ada data produk yang ditemukan.</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const currentUser = useState('user')
if (!currentUser.value) {
  navigateTo('/login')
}

const selectedBrand = useState('selectedBrand')
const uniqueBrandsState = useState('uniqueBrands')

// --- DUMMY DATA ---
const allProducts = [
  { brand: 'CA SKIN GLOW', sku: 'CAM001', name: 'Cooper Moisturizer 10 gr', stock: 500, inbound: 200 },
  { brand: 'CA SKIN GLOW', sku: 'CAS001', name: 'Cooper Peptide Luxe Serum', stock: 800, inbound: 150 },
  { brand: 'CA SKIN GLOW', sku: 'CASM001', name: 'White Truffle Serum Mist', stock: 15, inbound: 0 },
  { brand: 'Packaging Packing', sku: 'POLY01', name: 'Polymailer 17 x 30', stock: 10, inbound: 0 },
  { brand: 'Packaging Packing', sku: 'POLY02', name: 'Polymailer 30 x 30', stock: 5000, inbound: 1000 },
  { brand: 'Brand X', sku: 'BRX-001', name: 'Facial Wash Extra', stock: 120, inbound: 50 },
  { brand: 'Brand X', sku: 'BRX-002', name: 'Acne Toner', stock: 35, inbound: 0 }
]

uniqueBrandsState.value = ['Semua Brand', ...new Set(allProducts.map(item => item.brand))]

const filteredProducts = computed(() => {
  if (!currentUser.value) return []
  
  if (currentUser.value.role !== 'super_admin') {
    return allProducts.filter(p => p.brand === currentUser.value.assigned_brand)
  }
  
  if (selectedBrand.value === 'Semua Brand') return allProducts
  return allProducts.filter(p => p.brand === selectedBrand.value)
})

const totalStok = computed(() => filteredProducts.value.reduce((total, item) => total + item.stock, 0))
const totalInbound = computed(() => filteredProducts.value.reduce((total, item) => total + item.inbound, 0))
const lowStockCount = computed(() => filteredProducts.value.filter(item => item.stock < 50).length)
</script>
<template>
  <div class="pb-10 max-w-7xl mx-auto">
    <div class="mb-8 flex items-center">
      <div class="w-12 h-12 rounded-xl bg-green-50 text-green-600 flex items-center justify-center mr-4">
        <span class="material-symbols-outlined text-2xl">move_to_inbox</span>
      </div>
      <div>
        <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Penerimaan Barang (Inbound)</h2>
        <p class="text-sm text-gray-500 mt-1">Catat barang masuk dari supplier untuk menambah stok gudang.</p>
      </div>
    </div>
    
    <div class="flex flex-col lg:flex-row gap-6">
      <div class="w-full lg:w-1/3">
        <div class="bg-white rounded-2xl shadow-sm border border-gray-100 p-6 md:p-8 relative overflow-hidden">
          <span class="material-symbols-outlined absolute -right-6 -top-6 text-[8rem] text-blue-50 opacity-40 pointer-events-none">add_circle</span>
          
          <h3 class="font-bold text-gray-900 mb-6 border-b border-gray-100 pb-4 flex items-center relative z-10 text-lg">
            <span class="material-symbols-outlined mr-2 text-blue-600">edit_document</span> Form Input Inbound
          </h3>
          
          <form class="space-y-5 relative z-10">
            <div>
              <label class="block text-xs font-bold text-gray-500 uppercase tracking-wider mb-2">Pilih Brand</label>
              <select class="w-full border border-gray-200 rounded-xl p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none bg-gray-50 hover:bg-white transition-colors cursor-pointer text-gray-700 font-medium">
                <option>CA SKIN GLOW</option>
                <option>Packaging Packing</option>
                <option>Brand X</option>
              </select>
            </div>
            
            <div>
              <label class="block text-xs font-bold text-gray-500 uppercase tracking-wider mb-2">Pilih SKU Produk</label>
              <select class="w-full border border-gray-200 rounded-xl p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none bg-gray-50 hover:bg-white transition-colors cursor-pointer text-gray-700 font-medium">
                <option>CAS001 - Cooper Peptide Luxe Serum</option>
                <option>CAM001 - Cooper Moisturizer 10 gr</option>
              </select>
            </div>
            
            <div class="grid grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-bold text-gray-500 uppercase tracking-wider mb-2">Kuantitas</label>
                <input type="number" class="w-full border border-gray-200 rounded-xl p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none bg-gray-50 hover:bg-white transition-colors text-gray-700 font-medium" placeholder="0">
              </div>
              <div>
                <label class="block text-xs font-bold text-gray-500 uppercase tracking-wider mb-2">Tgl Masuk</label>
                <input type="date" class="w-full border border-gray-200 rounded-xl p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none bg-gray-50 hover:bg-white transition-colors text-gray-700 font-medium cursor-pointer" value="2026-03-27">
              </div>
            </div>
            
            <div>
              <label class="block text-xs font-bold text-gray-500 uppercase tracking-wider mb-2">Nama Supplier / Pabrik</label>
              <input type="text" class="w-full border border-gray-200 rounded-xl p-3 text-sm focus:ring-2 focus:ring-blue-500 focus:border-blue-500 outline-none bg-gray-50 hover:bg-white transition-colors text-gray-700 font-medium" placeholder="Contoh: PT. Makmur Skincare">
            </div>
            
            <button type="button" class="w-full bg-blue-600 text-white font-bold py-3.5 px-4 rounded-xl hover:bg-blue-700 transition-colors mt-4 flex justify-center items-center shadow-md shadow-blue-200">
              <span class="material-symbols-outlined mr-2">save</span> Simpan Stok
            </button>
          </form>
        </div>
      </div>

      <div class="w-full lg:w-2/3">
        <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden h-full flex flex-col">
          
          <div class="px-6 py-5 border-b border-gray-100 flex justify-between items-center">
            <h3 class="font-bold text-gray-900 flex items-center text-lg">
              <div class="w-8 h-8 rounded-lg bg-gray-50 text-gray-600 flex items-center justify-center mr-3">
                <span class="material-symbols-outlined text-sm">history</span>
              </div>
              Riwayat Hari Ini
            </h3>
            
            <NuxtLink to="/inbound-history" class="text-sm font-semibold text-blue-600 hover:text-blue-700 flex items-center gap-1 transition-colors bg-blue-50 px-4 py-2 rounded-lg hover:bg-blue-100 border border-blue-100">
              Lihat Semua Data
              <span class="material-symbols-outlined text-sm">arrow_forward</span>
            </NuxtLink>
          </div>
          
          <div class="overflow-x-auto w-full flex-1">
            <table class="w-full text-left min-w-[600px]">
              <thead class="bg-gray-50/50 text-gray-500 text-xs uppercase tracking-wider">
                <tr>
                  <th class="px-6 py-4 font-semibold">Waktu</th>
                  <th class="px-6 py-4 font-semibold">Brand</th>
                  <th class="px-6 py-4 font-semibold">SKU</th>
                  <th class="px-6 py-4 font-semibold text-right">Qty</th>
                  <th class="px-6 py-4 font-semibold">Supplier</th>
                </tr>
              </thead>
              <tbody class="text-sm divide-y divide-gray-100">
                <tr class="hover:bg-gray-50/80 transition-colors">
                  <td class="px-6 py-4 text-gray-500 text-xs font-medium">08:30 WIB</td>
                  <td class="px-6 py-4">
                    <span class="font-medium text-gray-800 bg-gray-100 px-2.5 py-1 rounded-md text-xs border border-gray-200">CA SKIN GLOW</span>
                  </td>
                  <td class="px-6 py-4 font-mono text-gray-500 text-xs">CASM001</td>
                  <td class="px-6 py-4 text-right">
                    <span class="font-bold text-green-600 bg-green-50 px-2.5 py-1 rounded-md border border-green-100">+500</span>
                  </td>
                  <td class="px-6 py-4 text-gray-700">Pabrik A</td>
                </tr>
                <tr class="hover:bg-gray-50/80 transition-colors">
                  <td class="px-6 py-4 text-gray-500 text-xs font-medium">10:15 WIB</td>
                  <td class="px-6 py-4">
                    <span class="font-medium text-gray-800 bg-gray-100 px-2.5 py-1 rounded-md text-xs border border-gray-200">Packaging Packing</span>
                  </td>
                  <td class="px-6 py-4 font-mono text-gray-500 text-xs">POLY02</td>
                  <td class="px-6 py-4 text-right">
                    <span class="font-bold text-green-600 bg-green-50 px-2.5 py-1 rounded-md border border-green-100">+1000</span>
                  </td>
                  <td class="px-6 py-4 text-gray-700">Supplier Plastik PT</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Proteksi Halaman
const currentUser = useState('user')
if (!currentUser.value) {
  navigateTo('/login')
}
</script>
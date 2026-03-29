<template>
  <div class="pb-10 max-w-7xl mx-auto">
    <div class="mb-8 flex items-center">
      <div class="w-12 h-12 rounded-xl bg-orange-50 text-orange-600 flex items-center justify-center mr-4">
        <span class="material-symbols-outlined text-2xl">qr_code_scanner</span>
      </div>
      <div>
        <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Proses Pengiriman (Outbound)</h2>
        <p class="text-sm text-gray-500 mt-1">Pindai resi/waybill untuk memotong stok secara otomatis berdasarkan platform.</p>
      </div>
    </div>
    
    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 p-8 md:p-12 mb-8 text-center relative overflow-hidden">
      <span class="material-symbols-outlined absolute -right-10 -bottom-10 text-[15rem] text-blue-50/50 pointer-events-none">barcode_scanner</span>
      <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-blue-400 via-blue-600 to-indigo-600"></div>
      
      <div class="relative z-10 max-w-2xl mx-auto">
        <div class="inline-flex items-center justify-center w-20 h-20 bg-blue-50 text-blue-600 rounded-2xl mb-6 shadow-inner border border-blue-100">
          <span class="material-symbols-outlined text-4xl">document_scanner</span>
        </div>
        
        <h3 class="text-xl md:text-2xl font-bold text-gray-900 mb-6">Arahkan Scanner ke Resi / Waybill</h3>
        
        <div class="relative max-w-lg mx-auto">
          <span class="material-symbols-outlined absolute left-5 top-1/2 transform -translate-y-1/2 text-gray-400 text-3xl">barcode</span>
          <input 
            type="text" 
            autofocus
            class="w-full text-center text-xl md:text-2xl tracking-[0.2em] font-mono border-2 border-gray-200 rounded-2xl py-4 md:py-5 pl-14 pr-6 focus:outline-none focus:border-blue-500 focus:ring-4 focus:ring-blue-500/10 transition-all shadow-sm text-gray-800 placeholder-gray-300" 
            placeholder="Klik & Scan Resi"
          >
        </div>
        
        <p class="text-gray-500 text-sm mt-5 flex items-center justify-center font-medium bg-gray-50 py-2 px-4 rounded-full w-fit mx-auto border border-gray-100">
          <span class="material-symbols-outlined text-[16px] mr-1.5 text-green-500">auto_awesome</span>
          Sistem akan mengenali SKU & Platform secara otomatis.
        </p>
      </div>
    </div>

    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden">
      <div class="px-6 py-5 border-b border-gray-100 flex justify-between items-center bg-white">
        <h3 class="font-bold text-gray-900 flex items-center text-lg">
          <div class="w-8 h-8 rounded-lg bg-gray-50 text-gray-600 flex items-center justify-center mr-3">
            <span class="material-symbols-outlined text-sm">list_alt</span>
          </div>
          Riwayat Scan Sesi Ini
        </h3>
        <span class="text-xs font-semibold text-gray-500 bg-gray-100 px-3 py-1.5 rounded-lg border border-gray-200">
          2 Resi Diproses
        </span>
      </div>
      
      <div class="overflow-x-auto w-full">
        <table class="w-full text-left min-w-[800px]">
          <thead class="bg-gray-50/50 text-gray-500 text-xs uppercase tracking-wider">
            <tr>
              <th class="px-6 py-4 font-semibold">Waktu</th>
              <th class="px-6 py-4 font-semibold">No. Resi (Waybill)</th>
              <th class="px-6 py-4 font-semibold">Ekspedisi</th>
              <th class="px-6 py-4 font-semibold">Platform</th>
              <th class="px-6 py-4 font-semibold">SKU Keluar</th>
              <th class="px-6 py-4 font-semibold text-center">Status</th>
            </tr>
          </thead>
          <tbody class="text-sm divide-y divide-gray-100">
            <tr class="hover:bg-gray-50/80 transition-colors">
              <td class="px-6 py-4 text-gray-500 text-xs font-medium">10:45:12 WIB</td>
              <td class="px-6 py-4 font-mono font-bold text-gray-900">JP8819203910</td>
              <td class="px-6 py-4">
                <span class="font-bold text-red-600 bg-red-50 px-2 py-1 rounded-md text-xs border border-red-100">J&T</span>
              </td>
              <td class="px-6 py-4">
                <span class="bg-[#ffede5] text-[#ee4d2d] border border-[#ffcdb8] px-2.5 py-1 rounded-md text-xs font-bold">Shopee</span>
              </td>
              <td class="px-6 py-4 font-mono text-gray-700">
                CAS001 <span class="text-red-500 font-bold ml-1 bg-red-50 px-1.5 py-0.5 rounded text-[10px]">-1</span>
              </td>
              <td class="px-6 py-4 flex justify-center">
                <span class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2.5 py-1 rounded-md text-xs font-bold w-full max-w-[100px] border border-green-100">
                  <span class="material-symbols-outlined text-[14px] mr-1">check_circle</span> Sukses
                </span>
              </td>
            </tr>
            <tr class="hover:bg-gray-50/80 transition-colors">
              <td class="px-6 py-4 text-gray-500 text-xs font-medium">10:43:05 WIB</td>
              <td class="px-6 py-4 font-mono font-bold text-gray-900">JX9901823111</td>
              <td class="px-6 py-4">
                <span class="font-bold text-red-600 bg-red-50 px-2 py-1 rounded-md text-xs border border-red-100">J&T</span>
              </td>
              <td class="px-6 py-4">
                <span class="bg-gray-900 text-white border border-gray-700 px-2.5 py-1 rounded-md text-xs font-bold">TikTok</span>
              </td>
              <td class="px-6 py-4 font-mono text-gray-700">
                CAM001 <span class="text-red-500 font-bold ml-1 bg-red-50 px-1.5 py-0.5 rounded text-[10px]">-2</span>
              </td>
              <td class="px-6 py-4 flex justify-center">
                <span class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2.5 py-1 rounded-md text-xs font-bold w-full max-w-[100px] border border-green-100">
                  <span class="material-symbols-outlined text-[14px] mr-1">check_circle</span> Sukses
                </span>
              </td>
            </tr>
          </tbody>
        </table>
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
<template>
  <div class="pb-10 max-w-7xl mx-auto">
    <div class="mb-6 md:mb-8 flex items-center">
      <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl bg-orange-50 text-orange-600 flex items-center justify-center mr-3 md:mr-4 shrink-0">
        <span class="material-symbols-outlined text-xl md:text-2xl">qr_code_scanner</span>
      </div>
      <div>
        <h2 class="text-xl md:text-2xl lg:text-3xl font-bold text-gray-900">Proses Pengiriman (Outbound)</h2>
        <p class="text-xs md:text-sm text-gray-500 mt-1">Pindai resi/waybill untuk memotong stok secara otomatis berdasarkan platform.</p>
      </div>
    </div>
    
    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 p-5 sm:p-8 md:p-12 mb-6 md:mb-8 text-center relative overflow-hidden">
      <span class="material-symbols-outlined absolute -right-6 -bottom-6 md:-right-10 md:-bottom-10 text-[10rem] md:text-[15rem] text-blue-50/50 pointer-events-none">barcode_scanner</span>
      <div class="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-blue-400 via-blue-600 to-indigo-600"></div>
      
      <div class="relative z-10 max-w-2xl mx-auto">
        <div class="inline-flex items-center justify-center w-16 h-16 md:w-20 md:h-20 bg-blue-50 text-blue-600 rounded-2xl mb-4 md:mb-6 shadow-inner border border-blue-100">
          <span class="material-symbols-outlined text-3xl md:text-4xl">document_scanner</span>
        </div>
        
        <h3 class="text-lg md:text-xl lg:text-2xl font-bold text-gray-900 mb-4 md:mb-6">Arahkan Scanner ke Resi / Waybill</h3>
        
        <div class="relative max-w-lg mx-auto">
          <span class="material-symbols-outlined absolute left-4 md:left-5 top-1/2 transform -translate-y-1/2 text-gray-400 text-2xl md:text-3xl">barcode</span>
          <input 
            type="text" 
            autofocus
            class="w-full text-center text-base md:text-xl lg:text-2xl tracking-widest md:tracking-[0.2em] font-mono border-2 border-gray-200 rounded-2xl py-3 md:py-4 lg:py-5 pl-12 md:pl-14 pr-4 md:pr-6 focus:outline-none focus:border-blue-500 focus:ring-4 focus:ring-blue-500/10 transition-all shadow-sm text-gray-800 placeholder-gray-300" 
            placeholder="Klik & Scan Resi"
          >
        </div>
        
        <p class="text-gray-500 text-[11px] md:text-sm mt-4 md:mt-5 flex items-center justify-center font-medium bg-gray-50 py-2 px-3 md:px-4 rounded-full w-fit mx-auto border border-gray-100">
          <span class="material-symbols-outlined text-[14px] md:text-[16px] mr-1 md:mr-1.5 text-green-500">auto_awesome</span>
          Sistem akan mengenali SKU & Platform otomatis.
        </p>
      </div>
    </div>

    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden">
      <div class="px-4 py-4 md:px-6 md:py-5 border-b border-gray-100 flex flex-col sm:flex-row sm:justify-between sm:items-center gap-3 bg-white">
        <h3 class="font-bold text-gray-900 flex items-center text-base md:text-lg">
          <div class="w-7 h-7 md:w-8 md:h-8 rounded-lg bg-gray-50 text-gray-600 flex items-center justify-center mr-2 md:mr-3 shrink-0">
            <span class="material-symbols-outlined text-sm">list_alt</span>
          </div>
          Riwayat Scan Sesi Ini
        </h3>
        <span class="text-[10px] md:text-xs font-semibold text-gray-500 bg-gray-100 px-2.5 py-1 md:px-3 md:py-1.5 rounded-lg border border-gray-200 w-fit">
          2 Resi Diproses
        </span>
      </div>
      
      <div class="overflow-x-auto w-full pb-2">
        <table class="w-full text-left min-w-[750px]">
          <thead class="bg-gray-50/50 text-gray-500 text-[10px] md:text-xs uppercase tracking-wider">
            <tr>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">Waktu</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">No. Resi (Waybill)</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">Ekspedisi</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">Platform</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold whitespace-nowrap">SKU Keluar</th>
              <th class="px-4 py-3 md:px-6 md:py-4 font-semibold text-center whitespace-nowrap">Status</th>
            </tr>
          </thead>
          <tbody class="text-xs md:text-sm divide-y divide-gray-100">
            <tr class="hover:bg-gray-50/80 transition-colors">
              <td class="px-4 py-3 md:px-6 md:py-4 text-gray-500 text-[11px] md:text-xs font-medium">10:45:12 WIB</td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono font-bold text-gray-900">JP8819203910</td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="font-bold text-red-600 bg-red-50 px-2 py-1 md:px-2 md:py-1 rounded-md text-[10px] md:text-xs border border-red-100">J&T</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="bg-[#ffede5] text-[#ee4d2d] border border-[#ffcdb8] px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs font-bold">Shopee</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono text-gray-700 text-[11px] md:text-sm">
                CAS001 <span class="text-red-500 font-bold ml-1 bg-red-50 px-1 py-0.5 md:px-1.5 md:py-0.5 rounded text-[9px] md:text-[10px]">-1</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 flex justify-center">
                <span class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[100px] border border-green-100">
                  <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1">check_circle</span> Sukses
                </span>
              </td>
            </tr>
            <tr class="hover:bg-gray-50/80 transition-colors">
              <td class="px-4 py-3 md:px-6 md:py-4 text-gray-500 text-[11px] md:text-xs font-medium">10:43:05 WIB</td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono font-bold text-gray-900">JX9901823111</td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="font-bold text-red-600 bg-red-50 px-2 py-1 md:px-2 md:py-1 rounded-md text-[10px] md:text-xs border border-red-100">J&T</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="bg-gray-900 text-white border border-gray-700 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs font-bold">TikTok</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono text-gray-700 text-[11px] md:text-sm">
                CAM001 <span class="text-red-500 font-bold ml-1 bg-red-50 px-1 py-0.5 md:px-1.5 md:py-0.5 rounded text-[9px] md:text-[10px]">-2</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 flex justify-center">
                <span class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2 py-1 md:px-2.5 md:py-1 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[100px] border border-green-100">
                  <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1">check_circle</span> Sukses
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
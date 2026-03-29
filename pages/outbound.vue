<template>
  <div class="pb-10 max-w-7xl mx-auto">
    <div class="mb-6 md:mb-8 flex items-center">
      <div class="w-10 h-10 md:w-12 md:h-12 rounded-xl bg-orange-50 text-orange-600 flex items-center justify-center mr-3 md:mr-4 shrink-0 shadow-sm border border-orange-100">
        <span class="material-symbols-outlined text-xl md:text-2xl">qr_code_scanner</span>
      </div>
      <div>
        <h2 class="text-xl md:text-2xl lg:text-3xl font-bold text-gray-900 tracking-tight">Proses Pengiriman (Outbound)</h2>
        <p class="text-xs md:text-sm text-gray-500 mt-1">Pindai resi/waybill untuk memotong stok secara otomatis berdasarkan platform.</p>
      </div>
    </div>
    
    <div class="bg-white rounded-[1.5rem] md:rounded-[2rem] shadow-lg shadow-gray-200/40 border border-gray-100 p-6 sm:p-8 md:p-12 lg:p-14 mb-8 md:mb-10 text-center relative overflow-hidden group">
      <span class="material-symbols-outlined absolute -right-6 -bottom-6 md:-right-16 md:-bottom-16 text-[10rem] md:text-[18rem] text-blue-50/40 pointer-events-none transition-transform duration-700 group-hover:scale-110">barcode_scanner</span>
      <div class="absolute top-0 left-0 w-full h-1.5 bg-gradient-to-r from-blue-400 via-indigo-500 to-purple-500"></div>
      <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-64 h-64 md:w-96 md:h-96 bg-blue-50/50 rounded-full blur-3xl -z-10 pointer-events-none"></div>
      
      <div class="relative z-10 max-w-2xl mx-auto">
        <div class="inline-flex items-center justify-center w-16 h-16 md:w-24 md:h-24 bg-gradient-to-br from-blue-50 to-indigo-50 text-blue-600 rounded-2xl md:rounded-3xl mb-6 md:mb-8 shadow-inner border border-white ring-1 ring-gray-100 relative">
          <span class="material-symbols-outlined text-3xl md:text-5xl relative z-10">document_scanner</span>
          <div class="absolute top-2 left-2 right-2 h-0.5 bg-blue-400 rounded-full opacity-50 shadow-[0_0_8px_2px_rgba(96,165,250,0.5)]"></div>
        </div>
        
        <h3 class="text-xl md:text-2xl lg:text-3xl font-extrabold text-gray-900 mb-6 md:mb-8 tracking-tight">Arahkan Scanner ke Resi</h3>
        
        <div class="relative max-w-xl mx-auto">
          <div class="absolute inset-0 bg-blue-500 rounded-xl md:rounded-2xl blur opacity-20 transition-opacity duration-300"></div>
          <div class="relative bg-white rounded-xl md:rounded-2xl">
            <span class="material-symbols-outlined absolute left-4 md:left-6 top-1/2 transform -translate-y-1/2 text-gray-400 text-2xl md:text-3xl">barcode</span>
            <input 
              type="text" 
              autofocus
              class="w-full text-center text-lg md:text-2xl lg:text-3xl tracking-[0.15em] md:tracking-[0.3em] font-mono border-2 border-gray-200 rounded-xl md:rounded-2xl py-4 md:py-6 pl-12 md:pl-16 pr-4 md:pr-6 focus:outline-none focus:border-blue-500 focus:ring-4 focus:ring-blue-500/10 transition-all shadow-sm text-gray-800 placeholder-gray-300 font-bold uppercase" 
              placeholder="KLIK & SCAN"
            >
          </div>
        </div>
        
        <div class="mt-6 md:mt-8 flex items-center justify-center">
          <div class="flex items-center bg-gray-50/80 backdrop-blur-sm py-2 px-4 md:px-5 rounded-full border border-gray-200 shadow-sm w-fit mx-auto md:mx-0">
            <span class="material-symbols-outlined text-[16px] md:text-[18px] mr-1.5 md:mr-2 text-green-500 animate-pulse">auto_awesome</span>
            <span class="text-gray-600 text-xs md:text-sm font-semibold text-center md:text-left">Sistem mengenali SKU & Platform otomatis</span>
          </div>
        </div>
      </div>
    </div>

    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden">
      <div class="px-4 py-4 md:px-6 md:py-5 border-b border-gray-100 flex flex-col sm:flex-row sm:justify-between sm:items-center gap-3 md:gap-4 bg-gray-50/50">
        <h3 class="font-bold text-gray-900 flex items-center text-base md:text-lg">
          <div class="w-7 h-7 md:w-8 md:h-8 rounded-lg bg-white text-gray-600 flex items-center justify-center mr-2 md:mr-3 shadow-sm border border-gray-100 shrink-0">
            <span class="material-symbols-outlined text-sm">list_alt</span>
          </div>
          Riwayat Scan Sesi Ini
        </h3>
        
        <div class="flex flex-row-reverse sm:flex-row items-center justify-between sm:justify-end gap-3 w-full sm:w-auto">
          <span class="text-[10px] md:text-xs font-bold text-gray-600 bg-white px-2.5 py-1.5 md:px-3 md:py-1.5 rounded-lg border border-gray-200 shadow-sm shrink-0">
            <span class="text-blue-600 mr-1">2</span> Diproses
          </span>
          
          <NuxtLink to="/outbound-history" class="text-xs md:text-sm font-semibold text-blue-600 hover:text-blue-700 flex items-center justify-center gap-1 transition-colors bg-blue-50 px-3 py-1.5 md:px-4 md:py-2 rounded-lg hover:bg-blue-100 border border-blue-100 w-full sm:w-auto">
            Lihat Semua Data
            <span class="material-symbols-outlined text-[14px] md:text-sm">arrow_forward</span>
          </NuxtLink>
        </div>
      </div>
      
      <div class="overflow-x-auto w-full pb-2">
        <table class="w-full text-left min-w-[750px] md:min-w-[800px]">
          <thead class="bg-white text-gray-500 text-[10px] md:text-[11px] uppercase tracking-wider md:tracking-widest">
            <tr>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold border-b border-gray-100 whitespace-nowrap">Waktu</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold border-b border-gray-100 whitespace-nowrap">No. Resi (Waybill)</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold border-b border-gray-100 whitespace-nowrap">Ekspedisi</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold border-b border-gray-100 whitespace-nowrap">Platform</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold border-b border-gray-100 whitespace-nowrap">SKU Keluar</th>
              <th class="px-4 py-3 md:px-6 md:py-5 font-bold border-b border-gray-100 text-center whitespace-nowrap">Status</th>
            </tr>
          </thead>
          <tbody class="text-xs md:text-sm divide-y divide-gray-50">
            <tr class="hover:bg-blue-50/30 transition-colors group">
              <td class="px-4 py-3 md:px-6 md:py-4 text-gray-500 text-[11px] md:text-xs font-medium">10:45:12 WIB</td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono font-bold text-gray-900 md:tracking-wide">JP8819203910</td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="font-bold text-red-600 bg-red-50 px-2 py-1 md:px-2.5 md:py-1.5 rounded-md text-[10px] md:text-xs border border-red-100">J&T</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="bg-[#ffede5] text-[#ee4d2d] border border-[#ffcdb8] px-2.5 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold shadow-sm">Shopee</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono text-gray-700 font-medium flex items-center text-[11px] md:text-sm">
                CAS001 
                <span class="text-white font-bold ml-1.5 md:ml-2 bg-red-500 px-1.5 py-0.5 rounded text-[9px] md:text-[10px] shadow-sm">-1</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <div class="flex justify-center">
                  <span class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[110px] border border-green-200 shadow-sm">
                    <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1 md:mr-1.5">check_circle</span> Sukses
                  </span>
                </div>
              </td>
            </tr>
            <tr class="hover:bg-blue-50/30 transition-colors group">
              <td class="px-4 py-3 md:px-6 md:py-4 text-gray-500 text-[11px] md:text-xs font-medium">10:43:05 WIB</td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono font-bold text-gray-900 md:tracking-wide">JX9901823111</td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="font-bold text-red-600 bg-red-50 px-2 py-1 md:px-2.5 md:py-1.5 rounded-md text-[10px] md:text-xs border border-red-100">J&T</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <span class="bg-gray-900 text-white border border-gray-700 px-2.5 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold shadow-sm">TikTok</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4 font-mono text-gray-700 font-medium flex items-center text-[11px] md:text-sm">
                CAM001 
                <span class="text-white font-bold ml-1.5 md:ml-2 bg-red-500 px-1.5 py-0.5 rounded text-[9px] md:text-[10px] shadow-sm">-2</span>
              </td>
              <td class="px-4 py-3 md:px-6 md:py-4">
                <div class="flex justify-center">
                  <span class="inline-flex items-center justify-center bg-green-50 text-green-700 px-2 py-1 md:px-3 md:py-1.5 rounded-md text-[10px] md:text-xs font-bold w-full max-w-[80px] md:max-w-[110px] border border-green-200 shadow-sm">
                    <span class="material-symbols-outlined text-[12px] md:text-[14px] mr-1 md:mr-1.5">check_circle</span> Sukses
                  </span>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
const currentUser = useState('user')
if (!currentUser.value) {
  navigateTo('/login')
}
</script>
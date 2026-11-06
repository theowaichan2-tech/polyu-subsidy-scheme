[Uploading index2.html…]()
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>PolyU Design — Competition/Award Subsidy Scheme Prototype</title>
  <!-- Tailwind CSS via CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brand: {
              cream: '#F6F4EE',
              card: '#FFFFFF',
              border: '#E8E5DC',
              borderLight: '#F0ECE3',
              dark: '#1C1B18',
              muted: '#737068',
              accentGreen: '#2E6B3E',
              accentGreenBg: '#E4EFE6',
              accentRed: '#B33A2B',
              accentRedBg: '#FAEAE6',
              accentOrange: '#966C1B',
              accentOrangeBg: '#FBF1E0',
              stepperDone: '#4D6142',
            }
          },
          fontFamily: {
            sans: ['Inter', '-apple-system', 'BlinkMacSystemFont', 'Segoe UI', 'Roboto', 'sans-serif'],
          }
        }
      }
    }
  </script>
  <style>
    /* Custom focus states for WCAG 2.1 AA compliance */
    input:focus-visible, select:focus-visible, textarea:focus-visible, button:focus-visible {
      outline: 2px solid #1C1B18;
      outline-offset: 2px;
    }
    /* Smooth transitions */
    .screen-container {
      transition: opacity 0.15s ease-in-out;
    }
  </style>
</head>
<body class="bg-[#F6F4EE] text-[#1C1B18] font-sans antialiased min-h-screen">

  <!-- ========================================================================= -->
  <!-- MOBILE DRAWER NAVIGATION (Shared across dashboard views)                  -->
  <!-- ========================================================================= -->
  <div id="mobile-drawer-backdrop" class="fixed inset-0 bg-black/40 z-40 hidden transition-opacity" onclick="toggleMobileMenu(false)"></div>
  <aside id="mobile-drawer" class="fixed top-0 left-0 bottom-0 w-72 bg-[#F5F2EB] z-50 transform -translate-x-full transition-transform duration-200 border-r border-[#E8E5DC] p-6 flex flex-col justify-between">
    <div>
      <div class="flex items-center justify-between pb-6 border-b border-[#E8E5DC]">
        <div>
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">PolyU School of Design</p>
          <p class="text-base font-bold text-[#1C1B18]">Subsidy Scheme</p>
        </div>
        <button onclick="toggleMobileMenu(false)" class="p-1 rounded-lg text-[#737068] hover:text-black">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>
        </button>
      </div>

      <div class="flex items-center space-x-3 py-4 border-b border-[#E8E5DC]">
        <div class="w-10 h-10 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-xs">HT</div>
        <div>
          <p class="text-xs font-bold text-[#1C1B18]">Hugo Tsang</p>
          <p class="text-[10px] text-[#737068]">Student applicant</p>
        </div>
      </div>

      <nav class="mt-4 space-y-1">
        <button onclick="navigateTo('screen-dashboard'); toggleMobileMenu(false)" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl bg-white shadow-sm font-semibold text-xs text-[#1C1B18]">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z"/></svg>
          <span>Dashboard</span>
        </button>
        <button onclick="navigateTo('screen-form-1'); toggleMobileMenu(false)" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068]">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/></svg>
          <span>New application</span>
        </button>
        <button onclick="navigateTo('screen-dashboard'); toggleMobileMenu(false)" class="w-full flex items-center justify-between px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068]">
          <div class="flex items-center space-x-3">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/></svg>
            <span>My applications</span>
          </div>
          <span class="text-[10px] bg-[#E8E5DC] text-[#1C1B18] px-1.5 py-0.5 rounded font-bold">4</span>
        </button>
        <button onclick="navigateTo('screen-reporting'); toggleMobileMenu(false)" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068]">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
          <span>Result reporting</span>
        </button>
        <button onclick="navigateTo('screen-help'); toggleMobileMenu(false)" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068]">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
          <span>Help & support</span>
        </button>
      </nav>
    </div>
    <div class="text-[11px] text-[#737068] pt-4 border-t border-[#E8E5DC]">
      PolyU School of Design • 2025/26
    </div>
  </aside>

  <!-- ========================================================================= -->
  <!-- SCREEN 1: 01_Student_Dashboard                                           -->
  <!-- ========================================================================= -->
  <section id="screen-dashboard" class="screen-container min-h-screen flex flex-col md:flex-row">
    <!-- Desktop Sidebar -->
    <aside class="hidden md:flex w-64 bg-[#EFECE3] border-r border-[#E8E5DC] flex-col justify-between shrink-0">
      <div>
        <div class="p-6 border-b border-[#E8E5DC]">
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">POLYU SCHOOL OF DESIGN</p>
          <h2 class="text-base font-bold tracking-tight text-[#1C1B18] mt-0.5">Subsidy Scheme</h2>
        </div>
        <nav class="p-4 space-y-1">
          <button onclick="navigateTo('screen-dashboard')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl bg-white shadow-sm font-semibold text-xs text-[#1C1B18]">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z"/></svg>
            <span>Dashboard</span>
          </button>
          <button onclick="navigateTo('screen-form-1')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/></svg>
            <span>New application</span>
          </button>
          <button onclick="navigateTo('screen-dashboard')" class="w-full flex items-center justify-between px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <div class="flex items-center space-x-3">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/></svg>
              <span>My applications</span>
            </div>
            <span class="text-[10px] bg-[#E8E5DC] text-[#1C1B18] px-1.5 py-0.5 rounded font-bold">4</span>
          </button>
          <button onclick="navigateTo('screen-reporting')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
            <span>Result reporting</span>
          </button>
          <button onclick="navigateTo('screen-help')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
            <span>Help & support</span>
          </button>
        </nav>
      </div>

      <!-- Bottom User Profile Card -->
      <div class="p-4 border-t border-[#E8E5DC]">
        <div class="flex items-center space-x-3 p-2 bg-white/70 rounded-xl">
          <div class="w-9 h-9 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-xs">HT</div>
          <div class="flex-1 min-w-0">
            <p class="text-xs font-bold text-[#1C1B18] truncate">Hugo Tsang</p>
            <p class="text-[10px] text-[#737068] truncate">Student applicant</p>
          </div>
          <span class="text-xs text-[#737068]">›</span>
        </div>
      </div>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <!-- Top Bar -->
      <header class="px-6 md:px-8 py-3.5 border-b border-[#E8E5DC] bg-[#F6F4EE]/90 backdrop-blur sticky top-0 z-20 flex items-center justify-between">
        <div class="flex items-center space-x-3">
          <button onclick="toggleMobileMenu(true)" class="md:hidden p-1.5 rounded-lg text-[#1C1B18] hover:bg-black/5" aria-label="Open Navigation Menu">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
          </button>
          <div class="md:hidden">
            <p class="font-bold text-xs">PolyU Design</p>
            <p class="text-[10px] text-[#737068]">Subsidy Scheme</p>
          </div>
          <span class="hidden md:inline text-xs text-[#737068]">Student portal • Dashboard</span>
        </div>

        <div class="flex items-center space-x-4">
          <button class="text-[#737068] hover:text-[#1C1B18]" aria-label="Search"><svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/></svg></button>
          <div class="relative">
            <button class="text-[#737068] hover:text-[#1C1B18]" aria-label="Notifications"><svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"/></svg></button>
            <span class="absolute -top-1 -right-0.5 w-1.5 h-1.5 bg-[#B33A2B] rounded-full"></span>
          </div>
          <div class="w-7 h-7 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-[10px]">HT</div>
        </div>
      </header>

      <div class="p-6 md:p-10 max-w-5xl mx-auto space-y-8">
        <!-- Hero Greeting -->
        <div>
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">SEP 2026 – AUG 2027 • YEAR 3</p>
          <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-[#1C1B18] mt-1">Good afternoon, Hugo.</h1>
          <p class="text-xs md:text-sm text-[#737068] mt-2">Here's where your subsidy applications stand today.</p>
          
          <!-- CTA BUTTON: HIDES SCREEN 1, REVEALS SCREEN 2 -->
          <div class="mt-4">
            <button id="btn-start-application" onclick="navigateTo('screen-form-1')" class="bg-[#1C1B18] hover:bg-black text-white text-xs font-semibold px-4 py-2.5 rounded-xl transition flex items-center space-x-2 shadow-sm">
              <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M12 4v16m8-8H4"/></svg>
              <span>Start a new application</span>
            </button>
          </div>
        </div>

        <!-- 3 Stat Metrics -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="bg-white p-5 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">ACTIVE APPLICATIONS</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">4</p>
            <p class="text-xs text-[#737068] mt-2">Across 3 competition bodies</p>
          </div>
          <div class="bg-white p-5 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">APPROVED FUNDING</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">HK$1,900</p>
            <p class="text-xs text-[#737068] mt-2">HK$8,100 remains this cycle</p>
          </div>
          <div class="bg-white p-5 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">NEXT DEADLINE</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">14 days</p>
            <p class="text-xs text-[#737068] mt-2">Report D&AD result by 12 Nov</p>
          </div>
        </div>

        <!-- Priority Queue -->
        <div>
          <div class="flex items-center justify-between mb-3">
            <div>
              <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">PRIORITY QUEUE</p>
              <h2 class="text-2xl font-bold tracking-tight text-[#1C1B18]">Needs your action</h2>
            </div>
            <span class="text-[10px] bg-[#FAEAE6] text-[#B33A2B] font-bold px-2 py-0.5 rounded-full">2 PENDING</span>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <!-- Priority Item 1 -->
            <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm flex flex-col justify-between">
              <div>
                <div class="flex items-center justify-between text-xs mb-3">
                  <div class="flex items-center space-x-2">
                    <span class="w-6 h-6 rounded-md bg-[#FAEAE6] text-[#B33A2B] flex items-center justify-center font-bold text-xs">📄</span>
                    <span class="uppercase font-bold text-[10px] tracking-wide text-[#B33A2B]">RETURNED FOR REVISION</span>
                  </div>
                  <span class="text-[11px] text-[#737068] font-medium">18 OCT</span>
                </div>
                <h3 class="text-base font-bold text-[#1C1B18]">Red Dot Design Award</h3>
                <p class="text-xs text-[#737068] mt-1 leading-relaxed">Confirm the group member student IDs, then resubmit for Prof. Karen Wong's endorsement.</p>
              </div>
              <div class="mt-6">
                <button onclick="navigateTo('screen-form-2')" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-4 py-2 rounded-xl transition flex items-center space-x-1.5">
                  <span>Revise application</span>
                  <span>→</span>
                </button>
              </div>
            </div>

            <!-- Priority Item 2 -->
            <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm flex flex-col justify-between">
              <div>
                <div class="flex items-center justify-between text-xs mb-3">
                  <div class="flex items-center space-x-2">
                    <span class="w-6 h-6 rounded-md bg-[#FBF1E0] text-[#966C1B] flex items-center justify-center font-bold text-xs">⏰</span>
                    <span class="uppercase font-bold text-[10px] tracking-wide text-[#966C1B]">RESULT DUE IN 14 DAYS</span>
                  </div>
                  <span class="text-[11px] text-[#737068] font-medium">12 NOV</span>
                </div>
                <h3 class="text-base font-bold text-[#1C1B18]">D&AD Awards</h3>
                <p class="text-xs text-[#737068] mt-1 leading-relaxed">Report the official result within one month of the announcement.</p>
              </div>
              <div class="mt-6">
                <button onclick="navigateTo('screen-reporting')" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-4 py-2 rounded-xl transition flex items-center space-x-1.5">
                  <span>Report result</span>
                  <span>→</span>
                </button>
              </div>
            </div>
          </div>
        </div>

        <!-- Application Tracker Table -->
        <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm">
          <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-4 pb-3 border-b border-[#E8E5DC]">
            <div>
              <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">APPLICATION TRACKER</p>
              <h3 class="text-xl font-bold text-[#1C1B18]">Your applications</h3>
            </div>
            <div class="flex items-center space-x-4 text-xs font-semibold">
              <span class="border-b-2 border-black pb-1 text-[#1C1B18] cursor-pointer">All</span>
              <span class="text-[#737068] hover:text-black cursor-pointer pb-1">Draft</span>
              <span class="text-[#737068] hover:text-black cursor-pointer pb-1">Endorsement</span>
              <span class="text-[#737068] hover:text-black cursor-pointer pb-1">Approved</span>
            </div>
          </div>

          <div class="divide-y divide-[#E8E5DC]">
            <!-- Row 1 -->
            <div onclick="navigateTo('screen-form-1')" class="py-3.5 flex items-center justify-between hover:bg-[#FAF8F5] px-2 rounded-xl transition cursor-pointer">
              <div class="space-y-0.5">
                <span class="text-[10px] text-[#737068]">SD-2026-018 • Updated 2 days ago</span>
                <p class="text-sm font-bold text-[#1C1B18]">Core77 Design Awards</p>
                <p class="text-xs text-[#737068]">Ripple — modular seating system</p>
              </div>
              <div class="flex items-center space-x-3">
                <span class="text-[10px] font-bold px-2.5 py-0.5 rounded-full bg-[#EFECE3] text-[#737068]">DRAFT</span>
                <span class="text-xs text-[#737068]">›</span>
              </div>
            </div>

            <!-- Row 2 -->
            <div onclick="navigateTo('screen-form-2')" class="py-3.5 flex items-center justify-between hover:bg-[#FAF8F5] px-2 rounded-xl transition cursor-pointer">
              <div class="space-y-0.5">
                <span class="text-[10px] text-[#737068]">SD-2026-014 • Returned 18 Oct 2026</span>
                <p class="text-sm font-bold text-[#1C1B18]">Red Dot Design Award</p>
                <p class="text-xs text-[#737068]">Lumen Bench — kinetic solar seating</p>
              </div>
              <div class="flex items-center space-x-3">
                <span class="text-[10px] font-bold px-2.5 py-0.5 rounded-full bg-[#FAEAE6] text-[#B33A2B]">RETURNED</span>
                <span class="text-xs text-[#737068]">›</span>
              </div>
            </div>

            <!-- Row 3 -->
            <div onclick="navigateTo('screen-reporting')" class="py-3.5 flex items-center justify-between hover:bg-[#FAF8F5] px-2 rounded-xl transition cursor-pointer">
              <div class="space-y-0.5">
                <span class="text-[10px] text-[#737068]">SD-2026-009 • Approved 04 Oct 2026</span>
                <p class="text-sm font-bold text-[#1C1B18]">D&AD Awards</p>
                <p class="text-xs text-[#737068]">Fold — editorial identity system</p>
              </div>
              <div class="flex items-center space-x-3">
                <span class="text-[10px] font-bold px-2.5 py-0.5 rounded-full bg-[#E4EFE6] text-[#2E6B3E]">APPROVED</span>
                <span class="text-xs text-[#737068]">›</span>
              </div>
            </div>

            <!-- Row 4 -->
            <div class="py-3.5 flex items-center justify-between hover:bg-[#FAF8F5] px-2 rounded-xl transition cursor-pointer">
              <div class="space-y-0.5">
                <span class="text-[10px] text-[#737068]">SD-2026-004 • Sent 26 Sep 2026</span>
                <p class="text-sm font-bold text-[#1C1B18]">iF Design Award</p>
                <p class="text-xs text-[#737068]">Nest — community learning toolkit</p>
              </div>
              <div class="flex items-center space-x-3">
                <span class="text-[10px] font-bold px-2.5 py-0.5 rounded-full bg-[#FBF1E0] text-[#966C1B]">ENDORSEMENT</span>
                <span class="text-xs text-[#737068]">›</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Bottom Allowance & Application Journey Widgets -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <!-- 2026/27 Cycle Allowance -->
          <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">2026/27 CYCLE ALLOWANCE</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">HK$8,100</p>
            <p class="text-xs text-[#737068] mt-0.5">REMAINING</p>

            <div class="w-full bg-[#E8E5DC] h-2 rounded-full overflow-hidden mt-4">
              <div class="bg-[#1C1B18] h-full w-[19%]"></div>
            </div>
            <div class="flex justify-between text-[11px] text-[#737068] mt-2 font-medium">
              <span>HK$1,900 approved</span>
              <span>HK$10,000 cap</span>
            </div>
            <p class="text-xs text-[#737068] mt-4 pt-3 border-t border-[#E8E5DC]">
              Shipping support is capped at HK$1,000 per application.
            </p>
          </div>

          <!-- Application Journey -->
          <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">HOW IT WORKS</p>
            <h3 class="text-xl font-bold text-[#1C1B18] mb-4">Your application journey</h3>
            <div class="space-y-3.5 text-xs">
              <div class="flex items-start space-x-3">
                <span class="w-5 h-5 rounded-full bg-[#4D6142] text-white flex items-center justify-center text-[10px] font-bold shrink-0">✓</span>
                <div>
                  <p class="font-bold text-[#1C1B18]">Prepare</p>
                  <p class="text-[#737068]">Build and save your draft</p>
                </div>
              </div>
              <div class="flex items-start space-x-3">
                <span class="w-5 h-5 rounded-full bg-[#FAF8F5] border border-[#E8E5DC] text-[#737068] flex items-center justify-center text-[10px] font-bold shrink-0">2</span>
                <div>
                  <p class="font-bold text-[#1C1B18]">Endorse</p>
                  <p class="text-[#737068]">Faculty reviews your request</p>
                </div>
              </div>
              <div class="flex items-start space-x-3">
                <span class="w-5 h-5 rounded-full bg-[#FAF8F5] border border-[#E8E5DC] text-[#737068] flex items-center justify-center text-[10px] font-bold shrink-0">3</span>
                <div>
                  <p class="font-bold text-[#1C1B18]">Verify</p>
                  <p class="text-[#737068]">SD Marketing checks eligibility</p>
                </div>
              </div>
              <div class="flex items-start space-x-3">
                <span class="w-5 h-5 rounded-full bg-[#FAF8F5] border border-[#E8E5DC] text-[#737068] flex items-center justify-center text-[10px] font-bold shrink-0">4</span>
                <div>
                  <p class="font-bold text-[#1C1B18]">Reimburse</p>
                  <p class="text-[#737068]">Submit receipts after approval</p>
                </div>
              </div>
            </div>
          </div>
        </div>

      </div>
    </main>
  </section>


  <!-- ========================================================================= -->
  <!-- SCREEN 2: 02_Application_Form_Step1 (PAGE 1 OF 3)                         -->
  <!-- ========================================================================= -->
  <section id="screen-form-1" class="screen-container hidden min-h-screen bg-[#F6F4EE] flex flex-col justify-between">
    <!-- Form Top Bar -->
    <header class="border-b border-[#E8E5DC] bg-white px-6 md:px-12 py-3.5 flex items-center justify-between sticky top-0 z-30">
      <div class="flex items-center space-x-3">
        <span class="font-bold text-sm tracking-tight text-[#1C1B18]">PolyU Design</span>
        <span class="text-xs text-[#737068] border-l border-[#E8E5DC] pl-3">Subsidy Scheme</span>
      </div>
      <div class="flex items-center space-x-4">
        <span class="hidden sm:inline text-xs text-[#737068]">Draft • Application ref pending</span>
        <button onclick="saveDraftAlert()" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-3 py-1.5 rounded-lg transition">Save draft</button>
        <!-- Cancel button returns to Screen 1 -->
        <button onclick="navigateTo('screen-dashboard')" class="text-[#737068] hover:text-black p-1 text-lg font-light leading-none" aria-label="Close and return to Dashboard">✕</button>
      </div>
    </header>

    <main class="max-w-4xl mx-auto w-full px-4 sm:px-6 py-8 flex-1 space-y-8">
      <!-- Title & Subtitle -->
      <div>
        <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">APPLICATION FORM • PAGE 1 OF 3</p>
        <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-[#1C1B18] mt-1">Your information</h1>
        <p class="text-xs md:text-sm text-[#737068] mt-2">Tell us who is applying and where you are in your PolyU Design studies.</p>
      </div>

      <!-- Horizontal Stepper (from mockups) -->
      <div class="py-3">
        <div class="relative flex items-center justify-between max-w-md mx-auto">
          <!-- Connecting Line -->
          <div class="absolute left-6 right-6 top-4 h-[1px] bg-[#D4CFBE] -z-0"></div>
          
          <!-- Step 1 Active -->
          <div class="flex flex-col items-center z-10">
            <div class="w-8 h-8 rounded-full bg-[#1C1B18] text-white flex items-center justify-center font-bold text-xs ring-4 ring-[#F6F4EE]">1</div>
            <span class="text-[11px] font-bold text-[#1C1B18] mt-2">Your information</span>
          </div>

          <!-- Step 2 -->
          <div class="flex flex-col items-center z-10">
            <div class="w-8 h-8 rounded-full bg-white border border-[#D4CFBE] text-[#737068] flex items-center justify-center font-semibold text-xs ring-4 ring-[#F6F4EE]">2</div>
            <span class="text-[11px] font-medium text-[#737068] mt-2">Competition & project</span>
          </div>

          <!-- Step 3 -->
          <div class="flex flex-col items-center z-10">
            <div class="w-8 h-8 rounded-full bg-white border border-[#D4CFBE] text-[#737068] flex items-center justify-center font-semibold text-xs ring-4 ring-[#F6F4EE]">3</div>
            <span class="text-[11px] font-medium text-[#737068] mt-2">Funding & declaration</span>
          </div>
        </div>
      </div>

      <!-- Form Card 1: Applicant Details -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Applicant details</h2>
          <span class="text-[11px] text-[#737068]">Fields marked * are required.</span>
        </div>

        <!-- Title radio pills -->
        <div>
          <label class="block text-xs font-semibold text-[#1C1B18] mb-2">Title *</label>
          <div class="flex space-x-3">
            <label class="flex items-center space-x-3 px-5 py-3 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5] transition">
              <input type="radio" name="applicant_title" value="Mr" checked class="w-4 h-4 text-black focus:ring-black">
              <span class="font-medium text-[#1C1B18]">Mr</span>
            </label>
            <label class="flex items-center space-x-3 px-5 py-3 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5] transition">
              <input type="radio" name="applicant_title" value="Ms" class="w-4 h-4 text-black focus:ring-black">
              <span class="font-medium text-[#1C1B18]">Ms</span>
            </label>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <label for="step1-fullname" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Full name *</label>
            <input type="text" id="step1-fullname" value="Hugo Tsang" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
          <div>
            <label for="step1-studentid" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Student ID *</label>
            <input type="text" id="step1-studentid" value="21098452D" placeholder="Enter student ID" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <label for="step1-phone" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Telephone number *</label>
            <input type="text" id="step1-phone" value="+852 9123 4567" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
          <div>
            <label for="step1-email" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Email *</label>
            <input type="email" id="step1-email" value="hugo.tsang@connect.polyu.hk" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
        </div>
      </div>

      <!-- Form Card 2: Study year & programme -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Study year & programme</h2>
          <span class="text-[11px] text-[#737068]">Select your current status and programme.</span>
        </div>

        <!-- Current study year selector -->
        <div>
          <label class="block text-xs font-semibold text-[#1C1B18] mb-2">Current study year *</label>
          <div class="grid grid-cols-2 sm:grid-cols-3 gap-3">
            <label class="flex items-center space-x-2.5 p-3.5 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="study_year" class="w-4 h-4 text-black">
              <span>Year 1</span>
            </label>
            <label class="flex items-center space-x-2.5 p-3.5 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="study_year" class="w-4 h-4 text-black">
              <span>Year 2</span>
            </label>
            <label class="flex items-center space-x-2.5 p-3.5 border-2 border-black bg-[#FAF8F5] rounded-xl text-xs font-bold cursor-pointer">
              <input type="radio" name="study_year" checked class="w-4 h-4 text-black">
              <span>Year 3</span>
            </label>
            <label class="flex items-center space-x-2.5 p-3.5 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="study_year" class="w-4 h-4 text-black">
              <span>Year 4</span>
            </label>
            <label class="flex items-center space-x-2.5 p-3.5 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5] col-span-2 sm:col-span-2">
              <input type="radio" name="study_year" class="w-4 h-4 text-black">
              <span>2025 graduate</span>
            </label>
          </div>
        </div>

        <div>
          <label for="step1-programme" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Programme *</label>
          <select id="step1-programme" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
            <option>BA (Hons) Scheme in Design — Product Design</option>
            <option>BA (Hons) Scheme in Design — Interaction Design</option>
            <option>BA (Hons) Scheme in Design — Communication Design</option>
            <option>BA (Hons) Scheme in Design — Advertising Design</option>
          </select>
        </div>

        <div>
          <label for="step1-progname" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Programme name (BA graduates only)</label>
          <input type="text" id="step1-progname" placeholder="Leave blank if not applicable" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
        </div>
      </div>
    </main>

    <!-- Sticky Bottom Navigation Bar: Step 1 -> Step 2 -->
    <footer class="border-t border-[#E8E5DC] bg-white py-4 px-6 md:px-12 sticky bottom-0 z-30 shadow-sm">
      <div class="max-w-4xl mx-auto flex items-center justify-between">
        <!-- Cancel button returns to Screen 1 as requested -->
        <button onclick="navigateTo('screen-dashboard')" class="text-xs font-semibold px-4 py-2.5 rounded-xl border border-[#E8E5DC] hover:bg-[#FAF8F5] text-[#737068] transition">
          Cancel
        </button>
        <span class="text-xs text-[#737068]">Page 1 of 3</span>
        <!-- Next Button hides Screen 2 and reveals Screen 3 -->
        <button id="btn-step1-continue" onclick="navigateTo('screen-form-2')" class="bg-[#1C1B18] hover:bg-black text-white text-xs font-semibold px-6 py-2.5 rounded-xl transition flex items-center space-x-2">
          <span>Continue</span>
          <span>→</span>
        </button>
      </div>
    </footer>
  </section>


  <!-- ========================================================================= -->
  <!-- SCREEN 3: 03_Application_Form_Step2 (PAGE 2 OF 3)                         -->
  <!-- ========================================================================= -->
  <section id="screen-form-2" class="screen-container hidden min-h-screen bg-[#F6F4EE] flex flex-col justify-between">
    <!-- Form Top Bar -->
    <header class="border-b border-[#E8E5DC] bg-white px-6 md:px-12 py-3.5 flex items-center justify-between sticky top-0 z-30">
      <div class="flex items-center space-x-3">
        <span class="font-bold text-sm tracking-tight text-[#1C1B18]">PolyU Design</span>
        <span class="text-xs text-[#737068] border-l border-[#E8E5DC] pl-3">Subsidy Scheme</span>
      </div>
      <div class="flex items-center space-x-4">
        <span class="hidden sm:inline text-xs text-[#737068]">Draft • Application ref pending</span>
        <button onclick="saveDraftAlert()" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-3 py-1.5 rounded-lg transition">Save draft</button>
        <button onclick="navigateTo('screen-dashboard')" class="text-[#737068] hover:text-black p-1 text-lg font-light leading-none" aria-label="Close">✕</button>
      </div>
    </header>

    <main class="max-w-4xl mx-auto w-full px-4 sm:px-6 py-8 flex-1 space-y-8">
      <div>
        <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">APPLICATION FORM • PAGE 2 OF 3</p>
        <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-[#1C1B18] mt-1">Competition & project</h1>
        <p class="text-xs md:text-sm text-[#737068] mt-2">Add the award information and identify the project being entered.</p>
      </div>

      <!-- Horizontal Stepper (Step 1 complete, Step 2 active) -->
      <div class="py-3">
        <div class="relative flex items-center justify-between max-w-md mx-auto">
          <div class="absolute left-6 right-6 top-4 h-[1px] bg-[#D4CFBE] -z-0"></div>
          
          <!-- Step 1 Complete -->
          <div class="flex flex-col items-center z-10 cursor-pointer" onclick="navigateTo('screen-form-1')">
            <div class="w-8 h-8 rounded-full bg-[#4D6142] text-white flex items-center justify-center font-bold text-xs ring-4 ring-[#F6F4EE]">✓</div>
            <span class="text-[11px] font-medium text-[#737068] mt-2">Your information</span>
          </div>

          <!-- Step 2 Active -->
          <div class="flex flex-col items-center z-10">
            <div class="w-8 h-8 rounded-full bg-[#1C1B18] text-white flex items-center justify-center font-bold text-xs ring-4 ring-[#F6F4EE]">2</div>
            <span class="text-[11px] font-bold text-[#1C1B18] mt-2">Competition & project</span>
          </div>

          <!-- Step 3 -->
          <div class="flex flex-col items-center z-10">
            <div class="w-8 h-8 rounded-full bg-white border border-[#D4CFBE] text-[#737068] flex items-center justify-center font-semibold text-xs ring-4 ring-[#F6F4EE]">3</div>
            <span class="text-[11px] font-medium text-[#737068] mt-2">Funding & declaration</span>
          </div>
        </div>
      </div>

      <!-- Form Card 1: Competition/Award information -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Competition/Award information</h2>
          <span class="text-[11px] text-[#737068]">Use the official published competition details.</span>
        </div>

        <div>
          <label for="step2-title" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Competition or award title *</label>
          <input type="text" id="step2-title" value="Red Dot Design Award: Design Concept" placeholder="e.g. Red Dot Design Award" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
        </div>

        <div>
          <label for="step2-url" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Official URL *</label>
          <input type="url" id="step2-url" value="https://www.red-dot.org/design-concept" placeholder="https://" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <label for="step2-category" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Category (if any)</label>
            <input type="text" id="step2-category" value="Sustainable Furniture & Public Space" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
          <div>
            <label for="step2-date" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Result announcement date *</label>
            <input type="date" id="step2-date" value="2026-11-20" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
        </div>

        <!-- Recognition level pills -->
        <div>
          <label class="block text-xs font-semibold text-[#1C1B18] mb-2">Recognition level *</label>
          <div class="grid grid-cols-3 gap-3">
            <label class="flex items-center space-x-2.5 p-3.5 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="recog_level" class="w-4 h-4 text-black">
              <span>Local</span>
            </label>
            <label class="flex items-center space-x-2.5 p-3.5 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="recog_level" class="w-4 h-4 text-black">
              <span>National</span>
            </label>
            <label class="flex items-center space-x-2.5 p-3.5 border-2 border-black bg-[#FAF8F5] rounded-xl text-xs font-bold cursor-pointer">
              <input type="radio" name="recog_level" checked class="w-4 h-4 text-black">
              <span>International</span>
            </label>
          </div>
        </div>
      </div>

      <!-- Form Card 2: Project details -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Project details</h2>
          <span class="text-[11px] text-[#737068]">Group members listed here must also be from SD.</span>
        </div>

        <div>
          <label for="step2-projecttitle" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Title of project *</label>
          <input type="text" id="step2-projecttitle" value="Lumen Bench — kinetic solar seating" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
        </div>

        <div>
          <label class="block text-xs font-semibold text-[#1C1B18] mb-2">Is it a group project? *</label>
          <div class="flex space-x-3">
            <label class="flex items-center space-x-3 px-5 py-3 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="is_group" value="No" class="w-4 h-4 text-black">
              <span class="font-medium text-[#1C1B18]">No</span>
            </label>
            <label class="flex items-center space-x-3 px-5 py-3 border-2 border-black bg-[#FAF8F5] rounded-xl text-xs font-bold cursor-pointer">
              <input type="radio" name="is_group" value="Yes" checked class="w-4 h-4 text-black">
              <span class="font-medium text-[#1C1B18]">Yes</span>
            </label>
          </div>
        </div>

        <div>
          <label class="block text-xs font-semibold text-[#1C1B18] mb-2">Is it coursework? *</label>
          <div class="flex space-x-3">
            <label class="flex items-center space-x-3 px-5 py-3 border-2 border-black bg-[#FAF8F5] rounded-xl text-xs font-bold cursor-pointer">
              <input type="radio" name="is_coursework" value="No" checked class="w-4 h-4 text-black">
              <span class="font-medium text-[#1C1B18]">No</span>
            </label>
            <label class="flex items-center space-x-3 px-5 py-3 border border-[#E8E5DC] rounded-xl text-xs cursor-pointer hover:bg-[#FAF8F5]">
              <input type="radio" name="is_coursework" value="Yes" class="w-4 h-4 text-black">
              <span class="font-medium text-[#1C1B18]">Yes</span>
            </label>
          </div>
        </div>
      </div>
    </main>

    <!-- Bottom Navigation Bar: Back to Step 1 OR Continue to Step 3 -->
    <footer class="border-t border-[#E8E5DC] bg-white py-4 px-6 md:px-12 sticky bottom-0 z-30 shadow-sm">
      <div class="max-w-4xl mx-auto flex items-center justify-between">
        <button onclick="navigateTo('screen-form-1')" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-5 py-2.5 rounded-xl transition">
          Back
        </button>
        <span class="text-xs text-[#737068]">Page 2 of 3</span>
        <button id="btn-step2-continue" onclick="navigateTo('screen-form-3')" class="bg-[#1C1B18] hover:bg-black text-white text-xs font-semibold px-6 py-2.5 rounded-xl transition flex items-center space-x-2">
          <span>Continue</span>
          <span>→</span>
        </button>
      </div>
    </footer>
  </section>


  <!-- ========================================================================= -->
  <!-- SCREEN 4: 03_Application_Form_Step2 (PAGE 3 OF 3: FUNDING & DECLARATION)  -->
  <!-- ========================================================================= -->
  <section id="screen-form-3" class="screen-container hidden min-h-screen bg-[#F6F4EE] flex flex-col justify-between">
    <!-- Form Top Bar -->
    <header class="border-b border-[#E8E5DC] bg-white px-6 md:px-12 py-3.5 flex items-center justify-between sticky top-0 z-30">
      <div class="flex items-center space-x-3">
        <span class="font-bold text-sm tracking-tight text-[#1C1B18]">PolyU Design</span>
        <span class="text-xs text-[#737068] border-l border-[#E8E5DC] pl-3">Subsidy Scheme</span>
      </div>
      <div class="flex items-center space-x-4">
        <span class="hidden sm:inline text-xs text-[#737068]">Draft • Application ref pending</span>
        <button onclick="saveDraftAlert()" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-3 py-1.5 rounded-lg transition">Save draft</button>
        <button onclick="navigateTo('screen-dashboard')" class="text-[#737068] hover:text-black p-1 text-lg font-light leading-none" aria-label="Close">✕</button>
      </div>
    </header>

    <main class="max-w-4xl mx-auto w-full px-4 sm:px-6 py-8 flex-1 space-y-8">
      <div>
        <p class="text-[10px] uppercase font-bold text-[#737068] tracking-wider">APPLICATION FORM • PAGE 3 OF 3</p>
        <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-[#1C1B18] mt-1">Funding & declaration</h1>
        <p class="text-xs md:text-sm text-[#737068] mt-2">Confirm the support requested, sign the declaration and send it for endorsement.</p>
      </div>

      <!-- Horizontal Stepper (Step 1 complete, Step 2 complete, Step 3 active) -->
      <div class="py-3">
        <div class="relative flex items-center justify-between max-w-md mx-auto">
          <div class="absolute left-6 right-6 top-4 h-[1px] bg-[#D4CFBE] -z-0"></div>
          
          <!-- Step 1 Complete -->
          <div class="flex flex-col items-center z-10 cursor-pointer" onclick="navigateTo('screen-form-1')">
            <div class="w-8 h-8 rounded-full bg-[#4D6142] text-white flex items-center justify-center font-bold text-xs ring-4 ring-[#F6F4EE]">✓</div>
            <span class="text-[11px] font-medium text-[#737068] mt-2">Your information</span>
          </div>

          <!-- Step 2 Complete -->
          <div class="flex flex-col items-center z-10 cursor-pointer" onclick="navigateTo('screen-form-2')">
            <div class="w-8 h-8 rounded-full bg-[#4D6142] text-white flex items-center justify-center font-bold text-xs ring-4 ring-[#F6F4EE]">✓</div>
            <span class="text-[11px] font-medium text-[#737068] mt-2">Competition & project</span>
          </div>

          <!-- Step 3 Active -->
          <div class="flex flex-col items-center z-10">
            <div class="w-8 h-8 rounded-full bg-[#1C1B18] text-white flex items-center justify-center font-bold text-xs ring-4 ring-[#F6F4EE]">3</div>
            <span class="text-[11px] font-bold text-[#1C1B18] mt-2">Funding & declaration</span>
          </div>
        </div>
      </div>

      <!-- Form Card 1: Applying for -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Applying for</h2>
          <span class="text-[11px] text-[#737068]">Select at least one type of support.</span>
        </div>

        <!-- Entrance fee checkbox -->
        <div class="p-4 rounded-xl border border-[#E8E5DC] bg-[#FAF8F5] space-y-3">
          <label class="flex items-center space-x-3 cursor-pointer">
            <input type="checkbox" id="check-fee-subsidy" checked class="w-4 h-4 rounded text-black focus:ring-black">
            <div>
              <p class="text-xs font-bold text-[#1C1B18]">Entrance fee subsidy</p>
              <p class="text-[11px] text-[#737068]">Enter the original fee currency and amount.</p>
            </div>
          </label>
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 pt-1">
            <input type="text" value="EUR 320" placeholder="e.g. EUR 320" class="text-xs px-3.5 py-2.5 rounded-lg border border-[#E8E5DC] bg-white">
            <input type="text" value="HK$ 2,750" placeholder="Approx HKD equivalent" class="text-xs px-3.5 py-2.5 rounded-lg border border-[#E8E5DC] bg-white">
          </div>
        </div>

        <!-- Shipping allowance checkbox & INPUT WITH VALIDATION RULE -->
        <div class="p-4 rounded-xl border border-[#E8E5DC] bg-[#FAF8F5] space-y-3">
          <label class="flex items-center space-x-3 cursor-pointer">
            <input type="checkbox" id="check-shipping-subsidy" checked class="w-4 h-4 rounded text-black focus:ring-black">
            <div>
              <p class="text-xs font-bold text-[#1C1B18]">Shipping allowance</p>
              <p class="text-[11px] text-[#737068]">Provide the estimated amount in HKD (capped at HK$1,000).</p>
            </div>
          </label>
          <div>
            <div class="relative">
              <span class="absolute left-3.5 top-2.5 text-xs font-semibold text-[#737068]">HK$</span>
              <input type="number" id="input-shipping-cost" value="850" class="w-full text-xs pl-12 pr-4 py-2.5 rounded-lg border border-[#E8E5DC] bg-white focus:outline-none focus:border-black font-semibold text-[#1C1B18]">
            </div>

            <!-- MANDATED ERROR MESSAGE: DISPLAYED IF SHIPPING > HK$1,000 -->
            <div id="shipping-error-alert" class="hidden mt-2 p-3 bg-[#FAEAE6] border border-[#B33A2B]/20 rounded-xl flex items-start space-x-2 text-xs text-[#B33A2B] font-medium">
              <span class="font-bold">⚠️</span>
              <span>The requested shipping amount exceeds the maximum allowance of HK$1,000. Please enter an amount of HK$1,000 or less to continue.</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Form Card 2: Declaration -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-4">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Declaration</h2>
          <span class="text-[11px] text-[#737068]">Both declarations are required before submission.</span>
        </div>

        <label class="flex items-start space-x-3 p-3.5 rounded-xl border border-[#E8E5DC] hover:bg-[#FAF8F5] cursor-pointer">
          <input type="checkbox" id="decl-complete" checked class="mt-0.5 w-4 h-4 text-black rounded focus:ring-black">
          <span class="text-xs text-[#1C1B18]">I confirm that the information in this application is complete and accurate.</span>
        </label>

        <label class="flex items-start space-x-3 p-3.5 rounded-xl border border-[#E8E5DC] hover:bg-[#FAF8F5] cursor-pointer">
          <input type="checkbox" id="decl-terms" checked class="mt-0.5 w-4 h-4 text-black rounded focus:ring-black">
          <span class="text-xs text-[#1C1B18]">I understand and agree to the terms and regulations of the Scheme.</span>
        </label>
      </div>

      <!-- Form Card 3: Signatures & Endorsement -->
      <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
        <div class="flex items-center justify-between border-b border-[#E8E5DC] pb-4">
          <h2 class="font-bold text-lg text-[#1C1B18]">Signatures & endorsement</h2>
          <span class="text-[11px] text-[#737068]">Your endorser will confirm their signature after submission.</span>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <label for="step3-signature" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Signature of applicant *</label>
            <input type="text" id="step3-signature" value="Hugo Tsang" placeholder="Type your full legal name" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
            <span class="text-[10px] text-[#737068] mt-1 block">Typing your name acts as your digital signature.</span>
          </div>
          <div>
            <label for="step3-date" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Date of application *</label>
            <input type="date" id="step3-date" value="2026-10-24" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
          </div>
        </div>

        <div>
          <label for="step3-endorser" class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Name of academic endorser *</label>
          <select id="step3-endorser" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white text-[#1C1B18] focus:border-black focus:ring-1 focus:ring-black">
            <option>Prof. Karen Wong — Discipline Leader (Product Design)</option>
            <option>Dr. Michael Leung — Assistant Professor</option>
            <option>Prof. Brian Lee — Associate Dean</option>
          </select>
        </div>

        <div class="p-3.5 bg-[#FAF8F5] border border-[#E8E5DC] rounded-xl flex items-center space-x-3 text-xs text-[#737068]">
          <span class="text-base">📄</span>
          <span>Signature of endorser: pending. The endorser will receive this application after you submit it.</span>
        </div>
      </div>
    </main>

    <!-- Bottom Navigation Bar: Submit Application CTA with Validation -->
    <footer class="border-t border-[#E8E5DC] bg-white py-4 px-6 md:px-12 sticky bottom-0 z-30 shadow-sm">
      <div class="max-w-4xl mx-auto flex items-center justify-between">
        <button onclick="navigateTo('screen-form-2')" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-5 py-2.5 rounded-xl transition">
          Back
        </button>
        <span class="text-xs text-[#737068]">Page 3 of 3</span>
        <!-- SUBMIT APPLICATION BUTTON: Validates shipping amount <= 1000 -->
        <button id="btn-submit-application" onclick="handleFormSubmission()" class="bg-[#1C1B18] hover:bg-black text-white text-xs font-semibold px-6 py-2.5 rounded-xl transition flex items-center space-x-2">
          <span>Submit Application</span>
          <span>→</span>
        </button>
      </div>
    </footer>
  </section>


  <!-- ========================================================================= -->
  <!-- SCREEN 5: 04_Success_Approved_Hub (SUBMISSION SUCCESS HUB)                -->
  <!-- ========================================================================= -->
  <section id="screen-success-hub" class="screen-container hidden min-h-screen bg-[#F6F4EE] flex flex-col justify-between">
    <!-- Top Header Bar -->
    <header class="border-b border-[#E8E5DC] bg-white px-6 md:px-12 py-3.5 flex items-center justify-between">
      <div class="flex items-center space-x-3">
        <span class="font-bold text-sm tracking-tight text-[#1C1B18]">PolyU Design</span>
        <span class="text-xs text-[#737068] border-l border-[#E8E5DC] pl-3">Subsidy Scheme</span>
      </div>
      <button onclick="navigateTo('screen-dashboard')" class="text-xs font-semibold text-[#737068] hover:text-black">
        Exit to dashboard
      </button>
    </header>

    <main class="max-w-2xl mx-auto w-full px-4 sm:px-6 py-12 flex-1 flex flex-col justify-center">
      <div class="bg-white p-8 md:p-12 rounded-3xl border border-[#E8E5DC] shadow-sm text-center space-y-6">
        <!-- Big Check Icon -->
        <div class="w-16 h-16 rounded-full bg-[#E4EFE6] text-[#2E6B3E] mx-auto flex items-center justify-center text-2xl font-bold">
          ✓
        </div>

        <div>
          <span class="inline-block px-3 py-1 rounded-full text-xs font-bold bg-[#E4EFE6] text-[#2E6B3E] uppercase tracking-wider mb-2">
            Status: Approved & Endorsement Logged
          </span>
          <h1 class="text-3xl md:text-4xl font-extrabold tracking-tight text-[#1C1B18]">Application Submitted!</h1>
          <p class="text-xs md:text-sm text-[#737068] mt-2 max-w-md mx-auto">
            Your application for the <strong class="text-[#1C1B18]">Red Dot Design Award</strong> has been confirmed and routed to <strong class="text-[#1C1B18]">Prof. Karen Wong</strong> for faculty endorsement.
          </p>
        </div>

        <!-- Receipt / Ref summary box -->
        <div class="p-5 rounded-2xl bg-[#FAF8F5] border border-[#E8E5DC] text-left space-y-3 text-xs">
          <div class="flex justify-between items-center border-b border-[#E8E5DC] pb-2">
            <span class="text-[#737068]">Application Reference</span>
            <span class="font-mono font-bold text-[#1C1B18]">SD-2026-021</span>
          </div>
          <div class="flex justify-between items-center border-b border-[#E8E5DC] pb-2">
            <span class="text-[#737068]">Applicant</span>
            <span class="font-semibold text-[#1C1B18]">Hugo Tsang (21098452D)</span>
          </div>
          <div class="flex justify-between items-center border-b border-[#E8E5DC] pb-2">
            <span class="text-[#737068]">Subsidy Amount Requested</span>
            <span class="font-semibold text-[#1C1B18]">HK$ 3,600 (Entrance Fee + Shipping)</span>
          </div>
          <div class="flex justify-between items-center">
            <span class="text-[#737068]">Next Action</span>
            <span class="font-semibold text-[#966C1B]">Endorsement review in 2-3 business days</span>
          </div>
        </div>

        <!-- Action CTA Button: Takes user back to Screen 1 as mandated -->
        <div class="pt-2">
          <button id="btn-return-dashboard" onclick="navigateTo('screen-dashboard')" class="w-full bg-[#1C1B18] hover:bg-black text-white text-xs font-semibold py-3.5 rounded-xl transition flex justify-center items-center space-x-2">
            <span>Return to Dashboard</span>
            <span>→</span>
          </button>
        </div>
      </div>
    </main>

    <footer class="py-6 text-center text-xs text-[#737068] border-t border-[#E8E5DC]">
      PolyU School of Design • Competition/Award Subsidy Scheme
    </footer>
  </section>


  <!-- ========================================================================= -->
  <!-- SCREEN 6: RESULT REPORTING (#screen-reporting)                            -->
  <!-- ========================================================================= -->
  <section id="screen-reporting" class="screen-container hidden min-h-screen flex flex-col md:flex-row">
    <!-- Desktop Sidebar -->
    <aside class="hidden md:flex w-64 bg-[#EFECE3] border-r border-[#E8E5DC] flex-col justify-between shrink-0">
      <div>
        <div class="p-6 border-b border-[#E8E5DC]">
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">POLYU SCHOOL OF DESIGN</p>
          <h2 class="text-base font-bold tracking-tight text-[#1C1B18] mt-0.5">Subsidy Scheme</h2>
        </div>
        <nav class="p-4 space-y-1">
          <button onclick="navigateTo('screen-dashboard')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z"/></svg>
            <span>Dashboard</span>
          </button>
          <button onclick="navigateTo('screen-form-1')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/></svg>
            <span>New application</span>
          </button>
          <button onclick="navigateTo('screen-dashboard')" class="w-full flex items-center justify-between px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <div class="flex items-center space-x-3">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/></svg>
              <span>My applications</span>
            </div>
            <span class="text-[10px] bg-[#E8E5DC] text-[#1C1B18] px-1.5 py-0.5 rounded font-bold">4</span>
          </button>
          <button onclick="navigateTo('screen-reporting')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl bg-white shadow-sm font-semibold text-xs text-[#1C1B18]">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
            <span>Result reporting</span>
          </button>
          <button onclick="navigateTo('screen-help')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
            <span>Help & support</span>
          </button>
        </nav>
      </div>

      <div class="p-4 border-t border-[#E8E5DC]">
        <div class="flex items-center space-x-3 p-2 bg-white/70 rounded-xl">
          <div class="w-9 h-9 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-xs">HT</div>
          <div class="flex-1 min-w-0">
            <p class="text-xs font-bold text-[#1C1B18] truncate">Hugo Tsang</p>
            <p class="text-[10px] text-[#737068] truncate">Student applicant</p>
          </div>
        </div>
      </div>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <header class="px-6 md:px-8 py-3.5 border-b border-[#E8E5DC] bg-[#F6F4EE]/90 backdrop-blur sticky top-0 z-20 flex items-center justify-between">
        <div class="flex items-center space-x-3">
          <button onclick="toggleMobileMenu(true)" class="md:hidden p-1.5 rounded-lg text-[#1C1B18] hover:bg-black/5">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
          </button>
          <span class="text-xs text-[#737068]">Student portal • Result reporting</span>
        </div>
        <div class="w-7 h-7 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-[10px]">HT</div>
      </header>

      <div class="p-6 md:p-10 max-w-4xl mx-auto space-y-8">
        <div>
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">POST-COMPETITION REQUIREMENT</p>
          <h1 class="text-4xl font-extrabold tracking-tight text-[#1C1B18] mt-1">Result reporting</h1>
          <p class="text-xs md:text-sm text-[#737068] mt-1">Report each official competition result within one month of its announcement.</p>
        </div>

        <!-- 3 Reporting metric summary cards -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="bg-white p-5 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068]">REPORTS DUE</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">1</p>
            <p class="text-xs text-[#737068] mt-2">Next due 12 Nov 2026</p>
          </div>
          <div class="bg-white p-5 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068]">AWAITING RESULT</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">1</p>
            <p class="text-xs text-[#737068] mt-2">Core77 Design Awards</p>
          </div>
          <div class="bg-white p-5 rounded-2xl border border-[#E8E5DC] shadow-sm">
            <p class="text-[10px] uppercase font-bold text-[#737068]">REPORTS SUBMITTED</p>
            <p class="text-3xl font-extrabold text-[#1C1B18] mt-2">1</p>
            <p class="text-xs text-[#737068] mt-2">Across this funding cycle</p>
          </div>
        </div>

        <!-- Queue Section -->
        <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-4">
          <p class="text-[10px] uppercase font-bold text-[#737068]">YOUR QUEUE</p>
          <h2 class="text-xl font-bold text-[#1C1B18]">Select an application</h2>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            <!-- Active Selected Card: D&AD -->
            <div class="p-5 rounded-xl border-2 border-black bg-[#FAF8F5] cursor-pointer">
              <div class="flex justify-between items-start">
                <span class="text-xs font-mono text-[#737068]">SD-2026-009</span>
                <span class="text-[10px] bg-[#FAEAE6] text-[#B33A2B] font-bold px-2 py-0.5 rounded-full">• DUE IN 14 DAYS</span>
              </div>
              <h4 class="font-bold text-base mt-2">D&AD Awards</h4>
              <p class="text-xs text-[#737068]">Fold — editorial identity system</p>
              <p class="text-[11px] text-[#737068] mt-3 font-medium">Report by 12 Nov 2026</p>
            </div>

            <!-- Inactive Card: Core77 -->
            <div class="p-5 rounded-xl border border-[#E8E5DC] opacity-70 hover:opacity-100 transition cursor-pointer">
              <div class="flex justify-between items-start">
                <span class="text-xs font-mono text-[#737068]">SD-2026-018</span>
                <span class="text-[10px] bg-[#FBF1E0] text-[#966C1B] font-bold px-2 py-0.5 rounded-full">• RESULT PENDING</span>
              </div>
              <h4 class="font-bold text-base mt-2">Core77 Design Awards</h4>
              <p class="text-xs text-[#737068]">Ripple — modular seating system</p>
              <p class="text-[11px] text-[#737068] mt-3">Report by 26 Dec 2026</p>
            </div>
          </div>

          <div class="pt-4 border-t border-[#E8E5DC] flex justify-between items-center text-xs text-[#737068]">
            <div>
              <span class="font-semibold text-[#1C1B18]">iF Design Award</span>
              <span class="ml-2">SD-2026-004 • Submitted 04 Oct 2026</span>
            </div>
            <span class="bg-[#E4EFE6] text-[#2E6B3E] text-[10px] font-bold px-2.5 py-0.5 rounded-full">● COMPLETE</span>
          </div>
        </div>

        <!-- Result reporting form -->
        <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-6">
          <div class="flex justify-between items-start border-b border-[#E8E5DC] pb-4">
            <div>
              <span class="text-xs font-mono text-[#737068]">SD-2026-009</span>
              <h2 class="text-2xl font-bold text-[#1C1B18]">D&AD Awards</h2>
              <p class="text-xs text-[#737068]">Fold — editorial identity system</p>
            </div>
            <span class="text-[10px] bg-[#FAEAE6] text-[#B33A2B] font-bold px-2.5 py-1 rounded-full">● DUE IN 14 DAYS</span>
          </div>

          <div class="space-y-4">
            <h3 class="font-bold text-sm text-[#1C1B18]">Official result</h3>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
              <div>
                <label class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Result outcome *</label>
                <select class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC] bg-white">
                  <option>Won an Award / Pencil</option>
                  <option>Shortlisted / Finalist</option>
                  <option>No award received</option>
                </select>
              </div>
              <div>
                <label class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Official announcement date *</label>
                <input type="date" value="2026-10-12" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC]">
              </div>
            </div>

            <div>
              <label class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Award title or result category</label>
              <input type="text" value="Wood Pencil — Graphic Design / Editorial" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC]">
            </div>
          </div>

          <div class="space-y-4 pt-4 border-t border-[#E8E5DC]">
            <h3 class="font-bold text-sm text-[#1C1B18]">Supporting evidence</h3>
            <div>
              <label class="block text-xs font-semibold text-[#1C1B18] mb-1.5">Official result URL</label>
              <input type="url" value="https://www.dandad.org/winners-2026/fold-identity" class="w-full text-xs px-4 py-3 rounded-xl border border-[#E8E5DC]">
            </div>

            <div class="border-2 border-dashed border-[#E8E5DC] rounded-2xl p-8 text-center hover:bg-[#FAF8F5] transition cursor-pointer">
              <span class="text-3xl block mb-2">📄</span>
              <p class="text-xs font-bold text-[#1C1B18]">Upload result evidence</p>
              <p class="text-[11px] text-[#737068] mt-0.5">PDF, JPG or PNG • maximum 10 MB</p>
            </div>
          </div>

          <div class="pt-4 border-t border-[#E8E5DC] space-y-4">
            <label class="flex items-start space-x-3 p-3.5 rounded-xl border border-[#E8E5DC] hover:bg-[#FAF8F5] cursor-pointer">
              <input type="checkbox" checked class="mt-0.5 w-4 h-4 text-black rounded focus:ring-black">
              <span class="text-xs text-[#737068]">I confirm that the result and supporting information provided are accurate and match the organiser's official announcement.</span>
            </label>

            <div class="flex justify-between items-center pt-2">
              <button onclick="navigateTo('screen-dashboard')" class="border border-[#E8E5DC] hover:bg-[#FAF8F5] text-xs font-semibold px-4 py-2.5 rounded-xl transition">
                Save draft
              </button>
              <button onclick="alert('Result report submitted successfully!'); navigateTo('screen-dashboard');" class="bg-[#1C1B18] hover:bg-black text-white text-xs font-semibold px-6 py-2.5 rounded-xl transition flex items-center space-x-2">
                <span>Submit result report</span>
                <span>→</span>
              </button>
            </div>
          </div>
        </div>

      </div>
    </main>
  </section>


  <!-- ========================================================================= -->
  <!-- SCREEN 7: HELP & SUPPORT (#screen-help)                                   -->
  <!-- ========================================================================= -->
  <section id="screen-help" class="screen-container hidden min-h-screen flex flex-col md:flex-row">
    <!-- Desktop Sidebar -->
    <aside class="hidden md:flex w-64 bg-[#EFECE3] border-r border-[#E8E5DC] flex-col justify-between shrink-0">
      <div>
        <div class="p-6 border-b border-[#E8E5DC]">
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">POLYU SCHOOL OF DESIGN</p>
          <h2 class="text-base font-bold tracking-tight text-[#1C1B18] mt-0.5">Subsidy Scheme</h2>
        </div>
        <nav class="p-4 space-y-1">
          <button onclick="navigateTo('screen-dashboard')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z"/></svg>
            <span>Dashboard</span>
          </button>
          <button onclick="navigateTo('screen-form-1')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/></svg>
            <span>New application</span>
          </button>
          <button onclick="navigateTo('screen-dashboard')" class="w-full flex items-center justify-between px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <div class="flex items-center space-x-3">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"/></svg>
              <span>My applications</span>
            </div>
            <span class="text-[10px] bg-[#E8E5DC] text-[#1C1B18] px-1.5 py-0.5 rounded font-bold">4</span>
          </button>
          <button onclick="navigateTo('screen-reporting')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl hover:bg-white/60 font-medium text-xs text-[#737068] transition">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
            <span>Result reporting</span>
          </button>
          <button onclick="navigateTo('screen-help')" class="w-full flex items-center space-x-3 px-3 py-2.5 rounded-xl bg-white shadow-sm font-semibold text-xs text-[#1C1B18]">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
            <span>Help & support</span>
          </button>
        </nav>
      </div>

      <div class="p-4 border-t border-[#E8E5DC]">
        <div class="flex items-center space-x-3 p-2 bg-white/70 rounded-xl">
          <div class="w-9 h-9 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-xs">HT</div>
          <div class="flex-1 min-w-0">
            <p class="text-xs font-bold text-[#1C1B18] truncate">Hugo Tsang</p>
            <p class="text-[10px] text-[#737068] truncate">Student applicant</p>
          </div>
        </div>
      </div>
    </aside>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <header class="px-6 md:px-8 py-3.5 border-b border-[#E8E5DC] bg-[#F6F4EE]/90 backdrop-blur sticky top-0 z-20 flex items-center justify-between">
        <div class="flex items-center space-x-3">
          <button onclick="toggleMobileMenu(true)" class="md:hidden p-1.5 rounded-lg text-[#1C1B18] hover:bg-black/5">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/></svg>
          </button>
          <span class="text-xs text-[#737068]">Student portal • Help & support</span>
        </div>
        <div class="w-7 h-7 rounded-full bg-[#4D5A43] text-white flex items-center justify-center font-bold text-[10px]">HT</div>
      </header>

      <div class="p-6 md:p-10 max-w-4xl mx-auto space-y-8">
        <!-- Hero Search Box -->
        <div class="bg-[#ECE7DD] rounded-3xl p-8 md:p-12 text-center space-y-4">
          <p class="text-[10px] uppercase font-bold tracking-wider text-[#737068]">STUDENT SUPPORT</p>
          <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-[#1C1B18]">How can we help?</h1>
          <p class="text-xs md:text-sm text-[#737068] max-w-md mx-auto">Find answers about applications, endorsements, reimbursements and result reporting.</p>
          <div class="max-w-md mx-auto relative pt-2">
            <span class="absolute left-4 top-5 text-[#737068]">🔍</span>
            <input type="text" placeholder="Search help articles" class="w-full text-xs pl-11 pr-4 py-3 rounded-full border border-[#D4CFBE] bg-white shadow-sm focus:outline-none focus:border-black">
          </div>
        </div>

        <!-- 3 Category cards -->
        <div>
          <p class="text-[10px] uppercase font-bold text-[#737068] mb-1">BROWSE BY TOPIC</p>
          <h2 class="text-xl font-bold text-[#1C1B18] mb-4">Start with a category</h2>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm flex flex-col justify-between space-y-4">
              <div>
                <span class="w-8 h-8 rounded-full bg-[#FAF8F5] border border-[#E8E5DC] flex items-center justify-center text-sm mb-3">📄</span>
                <h3 class="font-bold text-sm text-[#1C1B18]">Application & eligibility</h3>
                <p class="text-xs text-[#737068] mt-1 leading-relaxed">Who can apply, what is covered and how to prepare your form.</p>
              </div>
              <span class="text-xs font-semibold text-[#1C1B18]">View answers →</span>
            </div>

            <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm flex flex-col justify-between space-y-4">
              <div>
                <span class="w-8 h-8 rounded-full bg-[#FAF8F5] border border-[#E8E5DC] flex items-center justify-center text-sm mb-3">⏰</span>
                <h3 class="font-bold text-sm text-[#1C1B18]">Endorsement & decisions</h3>
                <p class="text-xs text-[#737068] mt-1 leading-relaxed">Faculty endorsement, review timing and returned revisions.</p>
              </div>
              <span class="text-xs font-semibold text-[#1C1B18]">View answers →</span>
            </div>

            <div class="bg-white p-6 rounded-2xl border border-[#E8E5DC] shadow-sm flex flex-col justify-between space-y-4">
              <div>
                <span class="w-8 h-8 rounded-full bg-[#FAF8F5] border border-[#E8E5DC] flex items-center justify-center text-sm mb-3">💳</span>
                <h3 class="font-bold text-sm text-[#1C1B18]">Reimbursement & results</h3>
                <p class="text-xs text-[#737068] mt-1 leading-relaxed">Receipts, approved payments and competition result reporting.</p>
              </div>
              <span class="text-xs font-semibold text-[#1C1B18]">View answers →</span>
            </div>
          </div>
        </div>

        <!-- FAQ Accordion -->
        <div class="bg-white p-6 md:p-8 rounded-2xl border border-[#E8E5DC] shadow-sm space-y-4">
          <p class="text-[10px] uppercase font-bold text-[#737068]">FREQUENTLY ASKED</p>
          <h2 class="text-xl font-bold text-[#1C1B18]">Common questions</h2>

          <div class="divide-y divide-[#E8E5DC]">
            <!-- Q1 -->
            <div class="py-4">
              <button onclick="toggleAccordion('faq-1')" class="w-full flex justify-between items-center text-left font-bold text-sm text-[#1C1B18]">
                <span>Who is eligible to apply for the subsidy scheme?</span>
                <span id="faq-1-icon" class="text-lg">−</span>
              </button>
              <div id="faq-1" class="mt-2 text-xs text-[#737068] leading-relaxed">
                Current full-time PolyU School of Design students may apply. Exchange students are not eligible. Group projects should be submitted by one student representative.
              </div>
            </div>

            <!-- Q2 -->
            <div class="py-4">
              <button onclick="toggleAccordion('faq-2')" class="w-full flex justify-between items-center text-left font-bold text-sm text-[#1C1B18]">
                <span>What expenses can I request support for?</span>
                <span id="faq-2-icon" class="text-lg">+</span>
              </button>
              <div id="faq-2" class="hidden mt-2 text-xs text-[#737068] leading-relaxed">
                Eligible expenses include entry fees (subsidised up to scheme maximums) and shipping costs (capped at HK$1,000 per application) for physical submissions.
              </div>
            </div>

            <!-- Q3 -->
            <div class="py-4">
              <button onclick="toggleAccordion('faq-3')" class="w-full flex justify-between items-center text-left font-bold text-sm text-[#1C1B18]">
                <span>Why was my application returned for revision?</span>
                <span id="faq-3-icon" class="text-lg">+</span>
              </button>
              <div id="faq-3" class="hidden mt-2 text-xs text-[#737068] leading-relaxed">
                Academic endorsers may return drafts if group member IDs need verification, proof of entry is missing, or budgets exceed the per-cycle allowance.
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  </section>


  <!-- ========================================================================= -->
  <!-- JAVASCRIPT CONTROLLER (SPA LOGIC & VALIDATION)                             -->
  <!-- ========================================================================= -->
  <script>
    /**
     * SPA Page Navigation Logic
     * Ensures all containers are hidden and target is displayed.
     */
    function navigateTo(targetScreenId) {
      const screens = document.querySelectorAll('.screen-container');
      screens.forEach(s => s.classList.add('hidden'));

      const target = document.getElementById(targetScreenId);
      if (target) {
        target.classList.remove('hidden');
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    }

    /**
     * Mobile Menu Drawer Toggle
     */
    function toggleMobileMenu(isOpen) {
      const drawer = document.getElementById('mobile-drawer');
      const backdrop = document.getElementById('mobile-drawer-backdrop');
      if (isOpen) {
        backdrop.classList.remove('hidden');
        drawer.classList.remove('-translate-x-full');
      } else {
        backdrop.classList.add('hidden');
        drawer.classList.add('-translate-x-full');
      }
    }

    /**
     * FAQ Accordion Toggle
     */
    function toggleAccordion(id) {
      const el = document.getElementById(id);
      const icon = document.getElementById(id + '-icon');
      if (el.classList.contains('hidden')) {
        el.classList.remove('hidden');
        icon.innerText = '−';
      } else {
        el.classList.add('hidden');
        icon.innerText = '+';
      }
    }

    /**
     * Save Draft Toast Simulation
     */
    function saveDraftAlert() {
      alert("Draft saved successfully! You can resume this application from your dashboard.");
    }

    /**
     * Screen 3 Form Submission & Validation Logic
     * Constraint: If shipping amount > HK$1,000, display red error message and prevent submission.
     * Otherwise, reveal Screen 4 (Success Hub).
     */
    function handleFormSubmission() {
      const shippingCheckbox = document.getElementById('check-shipping-subsidy');
      const shippingCostInput = document.getElementById('input-shipping-cost');
      const errorAlert = document.getElementById('shipping-error-alert');

      const amount = parseFloat(shippingCostInput.value) || 0;

      // Validation check
      if (shippingCheckbox.checked && amount > 1000) {
        errorAlert.classList.remove('hidden');
        shippingCostInput.classList.add('border-[#B33A2B]', 'ring-1', 'ring-[#B33A2B]');
        shippingCostInput.focus();
        return; // Prevent submission
      }

      // If valid, clear any error and transition to Screen 4 (04_Success_Approved_Hub)
      errorAlert.classList.add('hidden');
      shippingCostInput.classList.remove('border-[#B33A2B]', 'ring-1', 'ring-[#B33A2B]');
      navigateTo('screen-success-hub');
    }

    // Default entry: Screen 1 (01_Student_Dashboard) is visible by default
    document.addEventListener('DOMContentLoaded', () => {
      navigateTo('screen-dashboard');
    });
  </script>
</body>
</html>

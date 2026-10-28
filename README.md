<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>EduLearn - Kelas Digital Teks Anekdot</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    body { font-family: 'Plus Jakarta Sans', sans-serif; }
    .custom-scroll::-webkit-scrollbar { width: 4px; }
    .custom-scroll::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 4px; }
  </style>
</head>
<body class="bg-slate-100 text-slate-800 antialiased min-h-screen flex flex-col">

  <!-- ================= 1. LOGIN VIEW ================= -->
  <section id="view-auth" class="min-h-screen w-full flex items-center justify-center p-4 bg-slate-100">
    <div class="w-full max-w-4xl bg-white rounded-3xl shadow-xl overflow-hidden grid grid-cols-1 md:grid-cols-2 border border-slate-200/80">
      <div class="bg-gradient-to-br from-sky-700 via-sky-600 to-teal-700 p-8 text-white flex flex-col justify-between">
        <div>
          <div class="flex items-center gap-2 mb-8">
            <div class="w-10 h-10 rounded-2xl bg-white/20 backdrop-blur-md flex items-center justify-center font-black text-xl">🎓</div>
            <span class="text-xl font-extrabold tracking-tight">EduLearn</span>
          </div>
          <h2 class="text-3xl font-extrabold mb-3 leading-tight">Selamat Datang!</h2>
          <p class="text-sm text-sky-100 leading-relaxed">Portal pembelajaran digital terintegrasi materi Teks Anekdot, kuis interaktif, dan pengumpulan tugas terpusat.</p>
        </div>
        <div class="mt-8 text-xs text-sky-200/80">&copy; 2026 EduLearn Workspace System</div>
      </div>

      <div class="p-8 sm:p-10 flex flex-col justify-center">
        <h3 class="text-2xl font-bold text-slate-900 mb-1">Mulai Belajar</h3>
        <p class="text-xs text-slate-500 mb-6">Lengkapi data dirimu untuk mulai menjelajah kelas</p>

        <form id="loginForm" class="space-y-4">
          <div>
            <label class="block text-xs font-bold text-slate-600 mb-1">Nama Lengkap</label>
            <input type="text" id="authName" value="Ahmad Fauzi" required class="w-full px-4 py-2.5 rounded-xl border border-slate-300 text-sm focus:outline-none focus:ring-2 focus:ring-teal-500 font-medium" />
          </div>
          <div class="grid grid-cols-2 gap-3">
            <div>
              <label class="block text-xs font-bold text-slate-600 mb-1">Nomor Absen</label>
              <input type="text" id="authAbsen" value="05" required class="w-full px-4 py-2.5 rounded-xl border border-slate-300 text-sm focus:outline-none focus:ring-2 focus:ring-teal-500 font-medium" />
            </div>
            <div>
              <label class="block text-xs font-bold text-slate-600 mb-1">Pilihan Kelas</label>
              <select id="authClass" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 text-sm focus:outline-none focus:ring-2 focus:ring-teal-500 font-medium">
                <option value="XI-RPL 1">XI-RPL 1</option>
                <option value="XI-RPL 2">XI-RPL 2</option>
                <option value="X-Bahasa">X-Bahasa</option>
              </select>
            </div>
          </div>
          <button type="submit" class="w-full mt-2 py-3 bg-teal-600 hover:bg-teal-700 text-white font-bold rounded-xl text-sm transition shadow-md shadow-teal-600/20">
            Mulai Belajar &rarr;
          </button>
        </form>
      </div>
    </div>
  </section>

  <!-- ================= 2. DASHBOARD APP WORKSPACE ================= -->
  <div id="view-app" class="hidden min-h-screen flex flex-col md:flex-row">
    <!-- Sidebar -->
    <aside class="w-full md:w-64 bg-white border-r border-slate-200/80 flex flex-col shrink-0">
      <div class="h-20 px-6 flex items-center gap-3 border-b border-slate-100">
        <div class="w-10 h-10 rounded-2xl bg-gradient-to-tr from-sky-600 to-teal-500 flex items-center justify-center text-white font-black text-xl shadow-md shadow-teal-500/20">🎓</div>
        <div>
          <span class="font-black text-lg text-slate-900 tracking-tight">Edu<span class="text-teal-600">Learn</span></span>
          <span class="block text-[10px] text-slate-400 font-semibold tracking-wide">TEKS ANEKDOT</span>
        </div>
      </div>

      <nav class="p-4 space-y-1.5 flex-1">
        <button onclick="switchTab('dashboard')" id="nav-dashboard" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="layout-grid" class="w-5 h-5"></i> Dashboard
        </button>
        <button onclick="switchTab('materi')" id="nav-materi" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="book-open" class="w-5 h-5"></i> Materi
        </button>
        <button onclick="switchTab('video')" id="nav-video" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="play-square" class="w-5 h-5"></i> Video Pembelajaran
        </button>
        <button onclick="switchTab('absensi')" id="nav-absensi" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="calendar-check" class="w-5 h-5"></i> Absensi
        </button>
        <button onclick="switchTab('soal')" id="nav-soal" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="file-question" class="w-5 h-5"></i> Soal & Kuis
        </button>
        <button onclick="switchTab('tugas')" id="nav-tugas" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="clipboard-list" class="w-5 h-5"></i> Tugas (Kanban)
        </button>
        <button onclick="switchTab('pengumpulan')" id="nav-pengumpulan" class="nav-item w-full flex items-center gap-3 px-4 py-3 rounded-2xl text-sm font-bold text-slate-600 hover:bg-slate-50 transition">
          <i data-lucide="upload-cloud" class="w-5 h-5"></i> Pengumpulan Tugas
        </button>
      </nav>

      <div class="p-4 border-t border-slate-100 bg-slate-50/70">
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 rounded-full bg-teal-100 text-teal-700 flex items-center justify-center font-bold text-sm shrink-0" id="userAvatar">AF</div>
          <div class="overflow-hidden">
            <h4 class="text-xs font-bold text-slate-900 truncate" id="sideUserName">Ahmad Fauzi</h4>
            <p class="text-[10px] text-slate-500 truncate" id="sideUserClass">Kelas: XI-RPL 1 | Absen: 05</p>
          </div>
        </div>
      </div>
    </aside>

    <!-- Content Workspace -->
    <main class="flex-1 flex flex-col overflow-y-auto">
      <header class="h-20 bg-white border-b border-slate-200/80 px-6 flex items-center justify-between shrink-0">
        <div class="text-xs text-slate-500 font-medium">Semester Gasal 2026/2027 &bull; Bahasa Indonesia</div>
        <div class="flex items-center gap-4">
          <div class="text-right">
            <div class="text-xs font-bold text-slate-900" id="topUserName">Ahmad Fauzi</div>
            <div class="text-[10px] text-teal-600 font-semibold" id="topUserClass">XI-RPL 1 (05)</div>
          </div>
        </div>
      </header>

      <div class="p-6 md:p-8 space-y-6">

        <!-- TAB DASHBOARD -->
        <section id="tab-dashboard" class="tab-content space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
            <div>
              <h1 class="text-2xl font-black mb-1">Selamat Datang, <span class="student-name">Ahmad Fauzi</span>!</h1>
              <p class="text-xs text-sky-100">Lanjutkan modul pembelajaran Teks Anekdot hari ini.</p>
            </div>
            <div class="bg-white/20 backdrop-blur-md px-4 py-2 rounded-2xl text-xs font-bold border border-white/20 student-meta">
              Kelas: XI-RPL 1 | Absen: 05
            </div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm flex flex-col justify-between">
              <div>
                <h3 class="font-bold text-slate-900 text-base mb-1">Absensi Hari Ini</h3>
                <p class="text-xs text-slate-500 mb-4">Presensi harian siswa langsung tersimpan ke database Google Sheets.</p>
                <div id="dashAbsenStatus" class="inline-block px-3 py-1 rounded-full text-xs font-bold bg-amber-50 text-amber-700 border border-amber-200 mb-4">
                  ⚠️ Belum Absen
                </div>
              </div>
              <button onclick="lakukanAbsen()" class="w-full py-2.5 bg-sky-600 hover:bg-sky-700 text-white font-bold rounded-xl text-xs transition">
                Isi Kehadiran Sekarang
              </button>
            </div>

            <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm flex flex-col justify-between">
              <div>
                <div class="flex justify-between items-center mb-2">
                  <h3 class="font-bold text-slate-900 text-base">Tugas Terkini</h3>
                  <span class="text-[10px] font-bold text-rose-600 bg-rose-50 px-2.5 py-0.5 rounded-full border border-rose-200">Wajib</span>
                </div>
                <h4 class="font-bold text-sm text-slate-800 mb-1">Tugas 1: Analisis Struktur Teks Anekdot</h4>
                <p class="text-xs text-slate-500 mb-4">Unggah berkas analisis struktur dan kaidah kebahasaan.</p>
              </div>
              <button onclick="switchTab('pengumpulan')" class="w-full py-2.5 bg-teal-600 hover:bg-teal-700 text-white font-bold rounded-xl text-xs transition">
                Kumpulkan Berkas &rarr;
              </button>
            </div>

            <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm flex flex-col justify-between">
              <div>
                <h3 class="font-bold text-slate-900 text-base mb-1">Latihan Soal & Kuis</h3>
                <p class="text-xs text-slate-500 mb-4">10 Butir soal pilihan ganda otomatis terhubung dari spreadsheet pengajar.</p>
                <div class="text-xs font-bold text-slate-700 bg-slate-100 p-3 rounded-xl mb-4">
                  ⏱️ Durasi: 45 Menit | Auto-Koreksi
                </div>
              </div>
              <button onclick="switchTab('soal')" class="w-full py-2.5 bg-slate-900 hover:bg-slate-800 text-white font-bold rounded-xl text-xs transition">
                Mulai Kuis Soal &rarr;
              </button>
            </div>
          </div>
        </section>

        <!-- TAB MATERI -->
        <section id="tab-materi" class="tab-content hidden space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg flex justify-between items-center">
            <div>
              <h2 class="text-xl font-bold">Materi Pembelajaran</h2>
              <p class="text-xs text-sky-100">Bahasa Indonesia: Teks Anekdot</p>
            </div>
            <span class="text-xs font-bold bg-white/20 px-3 py-1.5 rounded-xl border border-white/20">Modul Tunggal</span>
          </div>

          <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <div class="space-y-4">
              <h3 class="text-xs font-bold text-slate-500 uppercase tracking-wider">Daftar Bab</h3>
              <div class="bg-white p-4 rounded-2xl border-2 border-teal-500 shadow-sm space-y-2">
                <span class="text-[10px] font-bold text-teal-700 bg-teal-50 px-2.5 py-0.5 rounded-full">Sedang Dibaca</span>
                <h4 class="text-sm font-bold text-slate-900" id="matSideJudul">Bab 1: Teks Anekdot</h4>
                <p class="text-xs text-slate-500 leading-relaxed" id="matSideDeskripsi">Memahami pengertian, ciri-ciri, struktur, dan kaidah kebahasaan.</p>
              </div>
            </div>

            <!-- Isi Materi Lengkap -->
            <div class="lg:col-span-2 bg-white p-6 md:p-8 rounded-3xl border border-slate-200/80 shadow-sm space-y-6">
              <div class="flex flex-col sm:flex-row sm:items-center justify-between pb-4 border-b border-slate-100 gap-3">
                <div>
                  <span class="text-xs font-bold text-teal-600 uppercase tracking-wider">Membaca Materi</span>
                  <h3 class="text-xl font-bold text-slate-900 mt-0.5" id="matMainJudul">Konsep & Struktur Teks Anekdot</h3>
                </div>
                <a id="btnDownloadPDF" href="#" target="_blank" class="hidden inline-flex items-center gap-2 px-4 py-2 bg-sky-600 hover:bg-sky-700 text-white font-bold text-xs rounded-xl transition">
                  <i data-lucide="download" class="w-4 h-4"></i> Unduh PDF Materi
                </a>
              </div>

              <div class="space-y-6 text-xs sm:text-sm text-slate-700 leading-relaxed">
                <!-- 1. Pengertian -->
                <div class="space-y-2">
                  <h4 class="font-bold text-slate-900 text-sm sm:text-base flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-teal-500"></span> 1. Pengertian Teks Anekdot
                  </h4>
                  <p><strong>Teks anekdot</strong> adalah cerita singkat yang lucu, menarik, dan berkesan, yang biasanya mengangkat kisah tentang tokoh penting atau kejadian sehari-hari, namun di baliknya tersimpan kritik sosial atau pesan moral.</p>
                  <div class="bg-teal-50 border border-teal-200 rounded-xl p-3 text-teal-900 text-xs">
                    <strong>Perbedaan dengan humor biasa:</strong> Humor murni hanya bertujuan menghibur, sedangkan anekdot selalu menyelipkan kritik atau sindiran halus terhadap fenomena sosial atau kebijakan.
                  </div>
                </div>

                <!-- 2. Ciri-Ciri -->
                <div class="space-y-3">
                  <h4 class="font-bold text-slate-900 text-sm sm:text-base flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-teal-500"></span> 2. Ciri-Ciri Teks Anekdot
                  </h4>
                  <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-xs">
                    <div class="p-3 bg-slate-50 border rounded-xl"><strong>😄 Menghibur:</strong> Dialog konyol atau situasi menggelitik.</div>
                    <div class="p-3 bg-slate-50 border rounded-xl"><strong>🎯 Menyindir:</strong> Mengkritik fenomena secara santun.</div>
                    <div class="p-3 bg-slate-50 border rounded-xl"><strong>💡 Menggelitik Pikiran:</strong> Mengajak pembaca merenung.</div>
                    <div class="p-3 bg-slate-50 border rounded-xl"><strong>📖 Cerita Nyata/Rekaan:</strong> Pengalaman nyata atau tokoh rekaan.</div>
                  </div>
                </div>

                <!-- 3. Struktur -->
                <div class="space-y-3">
                  <h4 class="font-bold text-slate-900 text-sm sm:text-base flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-teal-500"></span> 3. Struktur Teks Anekdot
                  </h4>
                  <ol class="space-y-2 border-l-2 border-teal-500 pl-4 text-xs">
                    <li><strong>1. Abstrak (Opsional):</strong> Gambaran awal isi cerita.</li>
                    <li><strong>2. Orientasi:</strong> Pengenalan tokoh, latar belakang, dan situasi.</li>
                    <li><strong>3. Krisis:</strong> Puncak konflik atau kejanggalan yang dialami tokoh.</li>
                    <li><strong>4. Reaksi:</strong> Tanggapan tokoh dalam merespons krisis (menghadirkan tawa).</li>
                    <li><strong>5. Koda (Opsional):</strong> Penutup berupa simpulan atau pesan moral.</li>
                  </ol>
                  <div class="text-[11px] text-slate-400 bg-slate-50 p-2 rounded-lg border">
                    *Kurikulum Merdeka sering menyingkat struktur menjadi <strong>OKE</strong> (Orientasi, Komplikasi, Evaluasi).
                  </div>
                </div>

                <!-- 4. Kaidah Kebahasaan -->
                <div class="space-y-3">
                  <h4 class="font-bold text-slate-900 text-sm sm:text-base flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-teal-500"></span> 4. Kaidah Kebahasaan
                  </h4>
                  <div class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-xs">
                    <div class="p-2.5 bg-white border rounded-xl"><strong>Kalimat Masa Lalu:</strong> Kejadian lampau.</div>
                    <div class="p-2.5 bg-white border rounded-xl"><strong>Kalimat Langsung:</strong> Dialog kutipan percakapan.</div>
                    <div class="p-2.5 bg-white border rounded-xl"><strong>Konjungsi Temporal:</strong> Urutan waktu (lalu, kemudian).</div>
                    <div class="p-2.5 bg-white border rounded-xl"><strong>Kata Kerja Aksi:</strong> Perbuatan fisik (menulis, tertawa).</div>
                    <div class="p-2.5 bg-white border rounded-xl"><strong>Kalimat Retoris:</strong> Pertanyaan sindiran tanpa jawaban.</div>
                    <div class="p-2.5 bg-white border rounded-xl"><strong>Majas Sindiran:</strong> Ironi, sinisme, atau sarkasme.</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </section>

        <!-- TAB VIDEO -->
        <section id="tab-video" class="tab-content hidden space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg">
            <h2 class="text-xl font-bold">Video Pembelajaran</h2>
            <p class="text-xs text-sky-100">Media visual penjelasan materi Teks Anekdot</p>
          </div>
          <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm space-y-4">
            <div class="w-full aspect-video bg-slate-900 rounded-2xl flex items-center justify-center text-white overflow-hidden">
              <iframe class="w-full h-full rounded-2xl" src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allowfullscreen></iframe>
            </div>
            <h3 class="font-bold text-slate-900 text-lg">Penjelasan Struktur & Contoh Teks Anekdot</h3>
            <p class="text-xs text-slate-500">Simak video ini untuk memahami bagaimana mengidentifikasi bagian krisis dan reaksi pada teks anekdot.</p>
          </div>
        </section>

        <!-- TAB ABSENSI -->
        <section id="tab-absensi" class="tab-content hidden space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg flex justify-between items-center">
            <div>
              <h2 class="text-xl font-bold">Absensi & Kehadiran</h2>
              <p class="text-xs text-sky-100">Data otomatis tersinkronisasi ke Google Sheets pengajar</p>
            </div>
            <div class="text-xs font-bold bg-white/20 px-3 py-1.5 rounded-xl student-meta">Kelas: XI-RPL 1 | Absen: 05</div>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm space-y-4">
              <h3 class="font-bold text-slate-900">Status Kehadiran Hari Ini</h3>
              <div id="absenBadge" class="p-4 bg-amber-50 border border-amber-200 rounded-2xl text-xs font-bold text-amber-800 flex items-center gap-2">
                ⚠️ Kamu belum mengisi kehadiran hari ini.
              </div>
              <button onclick="lakukanAbsen()" id="btnActionAbsen" class="w-full py-3 bg-teal-600 hover:bg-teal-700 text-white font-bold rounded-xl text-sm transition">
                Isi Kehadiran Hari Ini
              </button>
            </div>

            <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm space-y-4">
              <h3 class="font-bold text-slate-900">Riwayat Terakhir</h3>
              <table class="w-full text-left text-xs">
                <thead><tr class="border-b text-slate-400 font-semibold"><th class="pb-2">Waktu</th><th class="pb-2">Status</th></tr></thead>
                <tbody id="absenHistoryTable" class="divide-y divide-slate-100 font-medium">
                  <tr><td class="py-2.5">Belum ada rekapan sesi ini</td><td>-</td></tr>
                </tbody>
              </table>
            </div>
          </div>
        </section>

        <!-- TAB SOAL & KUIS -->
        <section id="tab-soal" class="tab-content hidden space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg flex justify-between items-center">
            <div>
              <h2 class="text-xl font-bold">Kuis & Ujian Mandiri</h2>
              <p class="text-xs text-sky-100">Butir soal terhubung langsung dari Google Sheets</p>
            </div>
            <div class="bg-rose-500/80 backdrop-blur-md px-3.5 py-1.5 rounded-xl text-xs font-bold text-white">
              Sisa Waktu: <span id="quizTimer">45:00</span>
            </div>
          </div>

          <div id="quizLoader" class="bg-white p-12 rounded-3xl border border-slate-200/80 text-center text-slate-500 font-bold text-sm">
            Memuat soal kuis dari Google Sheets... Mohon tunggu.
          </div>

          <div id="quizBox" class="hidden bg-white p-6 md:p-8 rounded-3xl border border-slate-200/80 shadow-sm space-y-6">
            <div class="border-b border-slate-100 pb-4">
              <span class="text-xs font-bold text-slate-500 block mb-2">Palet Nomor Soal:</span>
              <div id="quizPalette" class="flex flex-wrap gap-2"></div>
            </div>

            <div>
              <span id="labelNomorSoal" class="text-xs font-bold text-teal-600 uppercase tracking-wider block mb-1">Soal Nomor 1</span>
              <p id="teksPertanyaan" class="text-base sm:text-lg font-bold text-slate-900 leading-snug">-</p>
            </div>

            <div id="quizOptions" class="space-y-3"></div>

            <div class="flex justify-between items-center pt-4 border-t border-slate-100">
              <button onclick="stepSoal(-1)" id="btnSoalPrev" class="px-5 py-2.5 bg-slate-100 hover:bg-slate-200 font-bold text-slate-700 text-xs rounded-xl transition">
                &larr; Sebelumnya
              </button>
              <button onclick="stepSoal(1)" id="btnSoalNext" class="px-6 py-2.5 bg-teal-600 hover:bg-teal-700 font-bold text-white text-xs rounded-xl transition">
                Selanjutnya &rarr;
              </button>
            </div>
          </div>
        </section>

        <!-- TAB TUGAS (KANBAN) -->
        <section id="tab-tugas" class="tab-content hidden space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg">
            <h2 class="text-xl font-bold">Daftar Status Tugas</h2>
            <p class="text-xs text-sky-100">Pantau tugas mandiri Anda</p>
          </div>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div class="space-y-3">
              <h3 class="font-bold text-sm text-slate-700 flex items-center justify-between">
                <span>Belum Dikerjakan</span>
                <span class="w-5 h-5 rounded-full bg-slate-200 text-[10px] flex items-center justify-center font-bold">1</span>
              </h3>
              <div class="bg-white p-5 rounded-2xl border border-slate-200/80 shadow-sm space-y-2">
                <span class="text-[10px] font-bold text-rose-600 bg-rose-50 px-2 py-0.5 rounded">Tenggat Waktu: Besok</span>
                <h4 class="font-bold text-sm text-slate-900">Tugas 1: Analisis Struktur Anekdot</h4>
                <p class="text-xs text-slate-500">Menganalisis bagian Orientasi, Krisis, dan Reaksi pada teks contoh.</p>
                <button onclick="switchTab('pengumpulan')" class="w-full mt-2 py-1.5 bg-slate-900 hover:bg-slate-800 text-white font-bold text-xs rounded-lg transition">Kumpulkan Tugas</button>
              </div>
            </div>

            <div class="space-y-3">
              <h3 class="font-bold text-sm text-slate-700 flex items-center justify-between">
                <span>Sedang Dikerjakan</span>
                <span class="w-5 h-5 rounded-full bg-slate-200 text-[10px] flex items-center justify-center font-bold">0</span>
              </h3>
              <div class="p-6 border-2 border-dashed border-slate-200 rounded-2xl text-center text-xs text-slate-400">Tidak ada tugas aktif</div>
            </div>

            <div class="space-y-3">
              <h3 class="font-bold text-sm text-slate-700 flex items-center justify-between">
                <span>Selesai</span>
                <span class="w-5 h-5 rounded-full bg-slate-200 text-[10px] flex items-center justify-center font-bold">0</span>
              </h3>
              <div class="p-6 border-2 border-dashed border-slate-200 rounded-2xl text-center text-xs text-slate-400">Belum ada tugas selesai</div>
            </div>
          </div>
        </section>

        <!-- TAB PENGUMPULAN TUGAS (Langsung ke Google Drive) -->
        <section id="tab-pengumpulan" class="tab-content hidden space-y-6">
          <div class="p-6 rounded-3xl bg-gradient-to-r from-sky-600 to-teal-600 text-white shadow-lg flex justify-between items-center">
            <div>
              <h2 class="text-xl font-bold">Pengumpulan Tugas Online</h2>
              <p class="text-xs text-sky-100">File otomatis tersimpan di folder Google Drive pengajar</p>
            </div>
            <div class="text-xs font-bold bg-white/20 px-3 py-1.5 rounded-xl student-meta">Kelas: XI-RPL 1 | Absen: 05</div>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
            <div class="bg-white p-6 md:p-8 rounded-3xl border border-slate-200/80 shadow-sm">
              <h3 class="font-bold text-slate-900 text-base mb-1">Formulir Kirim Berkas</h3>
              <p class="text-xs text-slate-500 mb-6">Berkas akan diberi nama otomatis dan tercatat ke spreadsheet.</p>

              <form id="uploadTaskForm" class="space-y-4">
                <div>
                  <label class="block text-xs font-bold text-slate-600 mb-1">Pilih Tugas</label>
                  <select id="taskModulSelect" class="w-full px-4 py-2.5 rounded-xl border border-slate-300 text-xs font-medium focus:ring-2 focus:ring-teal-500">
                    <option value="Tugas1-Analisis-Anekdot">Tugas 1: Analisis Struktur Teks Anekdot</option>
                    <option value="Tugas2-Menulis-Anekdot">Tugas 2: Menulis Teks Anekdot Sendiri</option>
                  </select>
                </div>

                <div>
                  <label class="block text-xs font-bold text-slate-600 mb-1">Pilih Berkas (PDF, DOCX, ZIP, maks 10MB)</label>
                  <div class="border-2 border-dashed border-slate-300 hover:border-teal-500 rounded-2xl p-6 text-center cursor-pointer transition bg-slate-50/50" onclick="document.getElementById('taskFileInput').click()">
                    <i data-lucide="upload" class="w-8 h-8 text-slate-400 mx-auto mb-2"></i>
                    <p class="text-xs font-bold text-slate-700" id="fileLabelText">Tarik file ke sini atau klik untuk mencari berkas</p>
                    <p class="text-[10px] text-slate-400 mt-1">Maksimal 10 MB</p>
                  </div>
                  <input type="file" id="taskFileInput" class="hidden" required onchange="handleFileSelected(this)" />
                </div>

                <div class="bg-sky-50 border border-sky-200 rounded-2xl p-3.5 text-xs text-sky-900">
                  <span class="font-bold block mb-1">Format Nama Otomatis di Google Drive:</span>
                  <code class="text-[11px] font-mono bg-white px-2 py-1 rounded border border-sky-200 block truncate" id="previewAutoFilename">
                    [Tugas1-Analisis-Anekdot]_AhmadFauzi_Absen05_berkas.pdf
                  </code>
                </div>

                <button type="submit" id="btnSubmitDrive" class="w-full py-3 bg-teal-600 hover:bg-teal-700 text-white font-bold rounded-xl text-xs transition flex items-center justify-center gap-2">
                  <i data-lucide="cloud-upload" class="w-4 h-4"></i> Unggah ke Google Drive
                </button>
              </form>

              <div id="uploadFeedback" class="hidden mt-4 p-3 rounded-xl text-xs font-bold text-center"></div>
            </div>

            <div class="space-y-4">
              <div class="bg-white p-6 rounded-3xl border border-slate-200/80 shadow-sm space-y-3">
                <h4 class="font-bold text-slate-900 text-sm">Petunjuk Pengumpulan</h4>
                <ul class="text-xs text-slate-600 space-y-2 list-disc list-inside leading-relaxed">
                  <li>Siswa tidak perlu mengganti nama file, sistem akan menambahkan nama & nomor absen Anda secara otomatis.</li>
                  <li>File langsung masuk ke folder Google Drive pribadi milik pengajar secara privat.</li>
                </ul>
              </div>
            </div>
          </div>
        </section>

      </div>
    </main>
  </div>

  <script>
    // ==========================================
    // TEMPELKAN URL APPS SCRIPT ANDA DI BAWAH INI
    // ==========================================
    const SCRIPT_URL = "https://script.google.com/macros/s/AKfycbw9NauiCbomrDS0kqDEEm30rH7ygdOBKvfeSZsrPsiXw7XTGr1CjXQSrTJgs7Wd-NVO/exec";

    let currentUser = { name: "Ahmad Fauzi", absen: "05", kelas: "XI-RPL 1" };
    let bankSoal = [];
    let currentSoalIdx = 0;
    let jawabanSiswa = {};

    // 1. Auth / Login
    document.getElementById("loginForm").addEventListener("submit", function(e) {
      e.preventDefault();
      currentUser.name = document.getElementById("authName").value.trim() || "Ahmad Fauzi";
      currentUser.absen = document.getElementById("authAbsen").value.trim() || "05";
      currentUser.kelas = document.getElementById("authClass").value;

      updateUserUI();
      document.getElementById("view-auth").classList.add("hidden");
      document.getElementById("view-app").classList.remove("hidden");
      switchTab('dashboard');
      loadDataFromSheet();
    });

    function updateUserUI() {
      document.querySelectorAll(".student-name").forEach(el => el.innerText = currentUser.name);
      document.querySelectorAll(".student-meta").forEach(el => el.innerText = `Kelas: ${currentUser.kelas} | Absen: ${currentUser.absen}`);
      document.getElementById("sideUserName").innerText = currentUser.name;
      document.getElementById("sideUserClass").innerText = `Kelas: ${currentUser.kelas} | Absen: ${currentUser.absen}`;
      document.getElementById("topUserName").innerText = currentUser.name;
      document.getElementById("topUserClass").innerText = `${currentUser.kelas} (${currentUser.absen})`;
      document.getElementById("userAvatar").innerText = currentUser.name.split(" ").map(n => n[0]).slice(0, 2).join("");
    }

    // 2. Tab Navigation
    function switchTab(tabId) {
      document.querySelectorAll(".tab-content").forEach(el => el.classList.add("hidden"));
      const activeTab = document.getElementById(`tab-${tabId}`);
      if (activeTab) activeTab.classList.remove("hidden");

      document.querySelectorAll(".nav-item").forEach(btn => {
        btn.classList.remove("bg-teal-50", "text-teal-700", "font-extrabold");
        btn.classList.add("text-slate-600");
      });

      const activeNav = document.getElementById(`nav-${tabId}`);
      if (activeNav) {
        activeNav.classList.add("bg-teal-50", "text-teal-700", "font-extrabold");
        activeNav.classList.remove("text-slate-600");
      }
    }

    // 3. Absensi Real-time ke Sheets
    async function lakukanAbsen() {
      const btn = document.getElementById("btnActionAbsen");
      btn.disabled = true;
      btn.innerText = "Mencatat ke Google Sheets...";

      const now = new Date();
      const jamStr = now.toLocaleTimeString('id-ID', { hour: '2-digit', minute: '2-digit' }) + " WIB";

      try {
        if (!SCRIPT_URL.includes("TEMPEL_URL")) {
          await fetch(SCRIPT_URL, {
            method: "POST",
            mode: "no-cors",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify({
              action: "absen",
              nama: currentUser.name,
              kelas: currentUser.kelas,
              absen: currentUser.absen
            })
          });
        }

        document.getElementById("dashAbsenStatus").className = "inline-block px-3 py-1 rounded-full text-xs font-bold bg-emerald-50 text-emerald-700 border border-emerald-200 mb-4";
        document.getElementById("dashAbsenStatus").innerText = `✅ Hadir (${jamStr})`;

        document.getElementById("absenBadge").className = "p-4 bg-emerald-50 border border-emerald-200 rounded-2xl text-xs font-bold text-emerald-800 flex items-center gap-2";
        document.getElementById("absenBadge").innerText = `✅ Kehadiran berhasil tercatat di Google Sheets pengajar pukul ${jamStr}.`;
        btn.innerText = "Sudah Absen Hari Ini";
        btn.className = "w-full py-3 bg-slate-300 text-slate-500 font-bold rounded-xl text-sm cursor-not-allowed";

        const tr = document.createElement("tr");
        tr.innerHTML = `<td class="py-2.5 font-bold text-teal-800">Hari ini (${jamStr})</td><td><span class="px-2 py-0.5 rounded-full bg-emerald-50 text-emerald-700 font-bold">Hadir</span></td>`;
        document.getElementById("absenHistoryTable").innerHTML = "";
        document.getElementById("absenHistoryTable").appendChild(tr);

      } catch (e) {
        alert("Gagal mencatat absensi. Pastikan koneksi internet aktif.");
        btn.disabled = false;
        btn.innerText = "Isi Kehadiran Hari Ini";
      }
    }

    // 4. Memuat Soal & Materi dari Google Sheets
    async function loadDataFromSheet() {
      if (SCRIPT_URL.includes("TEMPEL_URL")) {
        // Fallback default
        bankSoal = [
          { id: 1, pertanyaan: "Manakah tujuan utama teks anekdot yang membedakannya dengan teks humor biasa?", opsi: { A: "Hanya menghibur pembaca", B: "Menyampaikan kritik sosial halus", C: "Menceritakan fiksi ilmiah", D: "Memberi instruksi kerja" }, kunci: "B" },
          { id: 2, pertanyaan: "Bagian struktur yang memuat puncak konflik atau kejanggalan adalah...", opsi: { A: "Orientasi", B: "Krisis", C: "Koda", D: "Abstrak" }, kunci: "B" }
        ];
        renderQuiz();
        return;
      }

      try {
        const res = await fetch(SCRIPT_URL);
        const data = await res.json();
        
        if (data.soal && data.soal.length > 0) {
          bankSoal = data.soal;
          renderQuiz();
        }

        if (data.materi && data.materi.length > 0) {
          const m = data.materi[0];
          document.getElementById("matSideJudul").innerText = m.bab;
          document.getElementById("matSideDeskripsi").innerText = m.deskripsi;
          document.getElementById("matMainJudul").innerText = m.judul;
          if (m.link_pdf) {
            const btn = document.getElementById("btnDownloadPDF");
            btn.href = m.link_pdf;
            btn.classList.remove("hidden");
          }
        }
      } catch (err) {
        console.error("Gagal memuat data dari spreadsheet", err);
        renderQuiz();
      }
    }

    function renderQuiz() {
      document.getElementById("quizLoader").classList.add("hidden");
      document.getElementById("quizBox").classList.remove("hidden");

      const palette = document.getElementById("quizPalette");
      palette.innerHTML = "";
      bankSoal.forEach((_, idx) => {
        const b = document.createElement("button");
        b.id = `pal-${idx}`;
        b.className = "w-8 h-8 rounded-lg text-xs font-bold border border-slate-200 bg-slate-50 text-slate-700";
        b.innerText = idx + 1;
        b.onclick = () => { currentSoalIdx = idx; tampilkanSoal(idx); };
        palette.appendChild(b);
      });

      tampilkanSoal(0);
    }

    function tampilkanSoal(idx) {
      const q = bankSoal[idx];
      document.getElementById("labelNomorSoal").innerText = `Soal Nomor ${idx + 1} dari ${bankSoal.length}`;
      document.getElementById("teksPertanyaan").innerText = q.pertanyaan;

      const ops = document.getElementById("quizOptions");
      ops.innerHTML = "";

      ["A", "B", "C", "D"].forEach(letter => {
        const isChoosen = jawabanSiswa[idx] === letter;
        const row = document.createElement("div");
        row.className = `p-3.5 border-2 rounded-2xl cursor-pointer flex items-center gap-3 transition ${isChoosen ? 'border-teal-600 bg-teal-50 font-bold text-teal-900' : 'border-slate-200 hover:border-slate-300 bg-white text-slate-800'}`;
        row.innerHTML = `<span class="w-7 h-7 rounded-full flex items-center justify-center text-xs font-black border ${isChoosen ? 'bg-teal-600 text-white border-teal-600' : 'border-slate-300 text-slate-400'}">${letter}</span> <span class="text-xs sm:text-sm">${q.opsi[letter]}</span>`;
        row.onclick = () => {
          jawabanSiswa[idx] = letter;
          document.getElementById(`pal-${idx}`).className = "w-8 h-8 rounded-lg text-xs font-bold bg-teal-600 text-white";
          tampilkanSoal(idx);
        };
        ops.appendChild(row);
      });

      document.getElementById("btnSoalPrev").disabled = idx === 0;
      document.getElementById("btnSoalNext").innerText = idx === bankSoal.length - 1 ? "Selesai Kuis" : "Selanjutnya →";
    }

    function stepSoal(direction) {
      const target = currentSoalIdx + direction;
      if (target >= 0 && target < bankSoal.length) {
        currentSoalIdx = target;
        tampilkanSoal(target);
      } else if (target === bankSoal.length) {
        alert("Kuis berhasil diselesaikan!");
      }
    }

    // 5. Upload Berkas ke Google Drive
    function handleFileSelected(input) {
      if (input.files && input.files[0]) {
        const file = input.files[0];
        document.getElementById("fileLabelText").innerText = `${file.name} (${(file.size / 1024 / 1024).toFixed(2)} MB)`;
        const modul = document.getElementById("taskModulSelect").value;
        const cleanName = currentUser.name.replace(/\s+/g, '');
        document.getElementById("previewAutoFilename").innerText = `[${modul}]_${cleanName}_Absen${currentUser.absen}_${file.name}`;
      }
    }

    document.getElementById("uploadTaskForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const fileInput = document.getElementById("taskFileInput");
      if (!fileInput.files.length) return;

      const file = fileInput.files[0];
      const btn = document.getElementById("btnSubmitDrive");
      const feedback = document.getElementById("uploadFeedback");

      btn.disabled = true;
      btn.innerText = "Mengunggah berkas ke Google Drive...";
      feedback.classList.remove("hidden", "bg-emerald-50", "text-emerald-800", "bg-rose-50", "text-rose-800");
      feedback.classList.add("bg-sky-50", "text-sky-800");
      feedback.innerText = "Sedang mengirim berkas ke folder Google Drive pengajar...";

      const reader = new FileReader();
      reader.readAsDataURL(file);
      reader.onload = async function() {
        const base64Data = reader.result.split(",")[1];
        const payload = {
          nama: currentUser.name,
          kelas: currentUser.kelas,
          absen: currentUser.absen,
          modul: document.getElementById("taskModulSelect").value,
          fileName: file.name,
          fileType: file.type || "application/octet-stream",
          fileBase64: base64Data
        };

        try {
          await fetch(SCRIPT_URL, {
            method: "POST",
            mode: "no-cors",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify(payload)
          });

          feedback.className = "mt-4 p-3 rounded-xl text-xs font-bold text-center bg-emerald-50 text-emerald-800 border border-emerald-200";
          feedback.innerText = "✅ Berkas berhasil tersimpan di Google Drive & link tercatat di Google Sheets!";
          fileInput.value = "";
          document.getElementById("fileLabelText").innerText = "Tarik file ke sini atau klik untuk mencari berkas";
        } catch (err) {
          console.error(err);
          feedback.className = "mt-4 p-3 rounded-xl text-xs font-bold text-center bg-rose-50 text-rose-800 border border-rose-200";
          feedback.innerText = "❌ Gagal mengunggah berkas. Periksa koneksi internet Anda.";
        } finally {
          btn.disabled = false;
          btn.innerHTML = `<i data-lucide="cloud-upload" class="w-4 h-4"></i> Unggah ke Google Drive`;
          lucide.createIcons();
        }
      };
    });

    lucide.createIcons();
  </script>
</body>
</html>

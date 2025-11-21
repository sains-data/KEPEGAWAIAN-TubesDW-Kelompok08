# 📄 Business Requirements Analysis
**Data Mart Kepegawaian - Institut Teknologi Sumatera**

---

## 1. Identifikasi Stakeholders

Pihak-pihak yang berkepentingan dan akan menggunakan hasil analisis dari Data Mart ini:

### Primary Stakeholders (Pengguna Utama)
* **Kepala Bagian Kepegawaian:** Menggunakan dashboard untuk pemantauan operasional harian (absensi) dan bulanan (gaji & kinerja).
* **Staff Kepegawaian:** Melakukan validasi data dan penarikan laporan detail.
* **Rektor dan Wakil Rektor II (SDM):** Menggunakan *high-level dashboard* untuk keputusan strategis terkait anggaran dan kebijakan SDM.

### Secondary Stakeholders (Pengguna Pendukung)
* **Kepala Fakultas / Kepala Biro:** Memantau kinerja dan kedisiplinan pegawai di unit kerja masing-masing.
* **Bagian Keuangan:** Memvalidasi rekapitulasi biaya gaji dan tunjangan (Costing).

---

## 2. Analisis Proses Bisnis (Business Process Scope)

Berdasarkan arsitektur *Galaxy Schema*, lingkup analisis mencakup tiga pilar utama:

### A. Manajemen Data & Biaya Pegawai (HR Profiling & Costing)
*Didukung oleh: `Fact_Employee_Snapshot`*
* **Pengelolaan Profil:** Analisis demografi pegawai berdasarkan Unit, Jabatan, Golongan, Gender, dan Usia.
* **Status Kepegawaian:** Pemantauan jumlah pegawai aktif (Headcount) vs Non-aktif (Resign/Pensiun).
* **Biaya SDM:** Rekapitulasi pengeluaran Gaji Pokok, Tunjangan, dan Potongan per unit kerja setiap bulan.

### B. Kehadiran & Kedisiplinan (Attendance)
*Didukung oleh: `Fact_Attendance`*
* **Absensi Harian:** Pemantauan jam masuk (*Check-in*) dan jam pulang (*Check-out*).
* **Keterlambatan:** Perhitungan intensitas keterlambatan (dalam menit) dibandingkan jam masuk resmi.
* **Durasi Kerja:** Analisis produktivitas waktu kerja efektif harian.
* **Pola Ketidakhadiran:** Analisis tren Sakit, Izin, dan Alpha.

### C. Kinerja Pegawai (Performance)
*Didukung oleh: `Fact_Performance`*
* **Evaluasi Berkala:** Analisis hasil penilaian kinerja (SKP & Perilaku) per semester/tahun.
* **Distribusi Grade:** Pemetaan pegawai berdasarkan predikat kinerja (A/B/C) untuk identifikasi *Top Talent* dan *Low Performer*.

---

## 3. Kebutuhan Analitik (KPIs)

Indikator kinerja kunci yang **DAPAT DIHITUNG** berdasarkan skema database yang telah dirancang:

### 🎯 Strategic KPIs (HR Health & Cost)
*Fokus: Biaya dan Profil (Bulanan)*
1.  **Total Headcount:** Jumlah total pegawai aktif pada periode berjalan.
2.  **Total Salary Cost:** Total biaya yang dikeluarkan untuk Gaji Pokok + Tunjangan.
3.  **Average Salary per Unit:** Rata-rata biaya gaji per pegawai di setiap Fakultas/Biro.
4.  **Turnover Count:** Jumlah pegawai yang statusnya berubah menjadi tidak aktif (Resign/Pensiun).
5.  **Average Tenure:** Rata-rata masa kerja pegawai (dihitung dari `TglMasuk` di Dimensi Pegawai).

### 📈 Operational KPIs (Discipline)
*Fokus: Kedisiplinan (Harian)*
1.  **Late Intensity (Menit):** Rata-rata menit keterlambatan per kejadian terlambat.
2.  **Punctuality Rate (%):** Persentase kehadiran tepat waktu vs total kehadiran.
3.  **Total Work Hours:** Total jam kerja efektif seluruh pegawai (untuk melihat beban kerja unit).
4.  **Absenteeism Rate:** Persentase ketidakhadiran (Sakit/Izin/Alpha) dibandingkan hari kerja efektif.

### ⭐ Performance KPIs (Quality)
*Fokus: Kualitas SDM (Semesteran)*
1.  **Average Performance Score:** Nilai rata-rata SKP/Total Skor seluruh pegawai.
2.  **High Performer Ratio (%):** Persentase pegawai dengan Grade 'A' (Sangat Baik).
3.  **Low Performer Ratio (%):** Persentase pegawai dengan Grade 'C' atau di bawahnya (Perlu Pembinaan).
4.  **Performance by Position:** Perbandingan rata-rata skor antara Dosen (Fungsional) vs Tendik (Struktural/Staff).

---

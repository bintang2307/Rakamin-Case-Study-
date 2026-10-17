# Rakamin-Case-Study-
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project Meridian - Workforce Capability & Redeployment Engine</title>
    <style>
        :root {
            --primary: #1e3a8a;
            --secondary: #2563eb;
            --accent: #f59e0b;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #0f172a;
            --text-muted: #64748b;
            --border: #e2e8f0;
            --danger: #ef4444;
            --success: #10b981;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--text-main);
            padding: 24px;
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            background-color: var(--primary);
            color: white;
            padding: 20px 24px;
            border-radius: 12px;
            margin-bottom: 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }

        header h1 {
            font-size: 20px;
            font-weight: 700;
        }

        header p {
            font-size: 13px;
            color: #93c5fd;
            margin-top: 4px;
        }

        .badge-bumn {
            background-color: rgba(255, 255, 255, 0.15);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 16px;
            margin-bottom: 24px;
        }

        .stat-card {
            background: var(--card-bg);
            padding: 16px 20px;
            border-radius: 10px;
            border: 1px solid var(--border);
        }

        .stat-card .label {
            font-size: 12px;
            color: var(--text-muted);
            text-transform: uppercase;
            font-weight: 600;
        }

        .stat-card .value {
            font-size: 24px;
            font-weight: 700;
            margin-top: 6px;
        }

        .stat-card .sub {
            font-size: 12px;
            margin-top: 4px;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        .panel {
            background: var(--card-bg);
            border-radius: 12px;
            border: 1px solid var(--border);
            padding: 20px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }

        .panel-title {
            font-size: 16px;
            font-weight: 700;
            margin-bottom: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .employee-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .employee-card {
            border: 1px solid var(--border);
            padding: 14px 16px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s ease;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .employee-card:hover {
            border-color: var(--secondary);
            background-color: #f0f6ff;
        }

        .employee-card.active {
            border-color: var(--secondary);
            background-color: #eff6ff;
            box-shadow: 0 0 0 2px rgba(37, 99, 235, 0.2);
        }

        .emp-info h4 {
            font-size: 14px;
            font-weight: 600;
        }

        .emp-info p {
            font-size: 12px;
            color: var(--text-muted);
            margin-top: 2px;
        }

        .emp-risk {
            text-align: right;
        }

        .risk-tag {
            display: inline-block;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 11px;
            font-weight: 700;
        }

        .risk-high {
            background-color: #fef2f2;
            color: var(--danger);
            border: 1px solid #fecaca;
        }

        /* Detail Panel & AHA Moment */
        .detail-placeholder {
            text-align: center;
            padding: 40px 20px;
            color: var(--text-muted);
            font-size: 14px;
        }

        .aha-card {
            background: linear-gradient(135deg, #eff6ff 0%, #e0e7ff 100%);
            border: 2px solid var(--secondary);
            border-radius: 10px;
            padding: 20px;
            margin-top: 16px;
            position: relative;
            overflow: hidden;
        }

        .aha-badge {
            position: absolute;
            top: 12px;
            right: 12px;
            background: var(--accent);
            color: #000;
            font-size: 10px;
            font-weight: 800;
            padding: 4px 8px;
            border-radius: 12px;
            text-transform: uppercase;
        }

        .aha-title {
            font-size: 15px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 8px;
        }

        .match-score {
            font-size: 28px;
            font-weight: 800;
            color: var(--secondary);
            margin: 8px 0;
        }

        .reskill-timeline {
            margin-top: 12px;
            padding-top: 12px;
            border-top: 1px solid rgba(0,0,0,0.1);
            font-size: 13px;
        }

        .btn-action {
            display: block;
            width: 100%;
            background-color: var(--secondary);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-weight: 600;
            margin-top: 16px;
            cursor: pointer;
            text-align: center;
            transition: background 0.2s;
        }

        .btn-action:hover {
            background-color: var(--primary);
        }
    </style>
</head>
<body>

    <header>
        <div>
            <h1>Project Meridian — Capability Engine</h1>
            <p>BUMN Energy Talent Transformation & AI Displacement Mitigation</p>
        </div>
        <div class="badge-bumn">CONFIDENTIAL — BOARD LEVEL</div>
    </header>

    <div class="stats-grid">
        <div class="stat-card">
            <div class="label">Total Pekerja Terpengaruh</div>
            <div class="value" style="color: var(--danger);">4,200</div>
            <div class="sub" style="color: var(--danger);">Field Metering (Otomatisasi 70%)</div>
        </div>
        <div class="stat-card">
            <div class="label">Mandat Kebijakan</div>
            <div class="value" style="color: var(--success);">0 Layoff</div>
            <div class="sub" style="color: var(--success);">100% Internal Reskilling</div>
        </div>
        <div class="stat-card">
            <div class="label">Target Waktu Board</div>
            <div class="value" style="color: var(--secondary);">90 Hari</div>
            <div class="sub" style="color: var(--text-muted);">Transisi Berbasis Kapabilitas</div>
        </div>
        <div class="stat-card">
            <div class="label">Estimasi Penghematan</div>
            <div class="value" style="color: var(--primary);">Rp 437.5 M</div>
            <div class="sub" style="color: var(--text-muted);">Rencana Efisiensi Vendor</div>
        </div>
    </div>

    <div class="main-content">
        <!-- Panel Kiri: Daftar Sampel Karyawan -->
        <div class="panel">
            <div class="panel-title">
                <span>Sampel Pegawai Terdampak AI</span>
                <span style="font-size: 12px; font-weight: normal; color: var(--text-muted);">Pilih untuk Simulasi</span>
            </div>
            <div class="employee-list" id="employeeList">
                <!-- Data diisi oleh JavaScript -->
            </div>
        </div>

        <!-- Panel Kanan: Momen AHA / Hasil Matching -->
        <div class="panel" id="detailPanel">
            <div class="detail-placeholder">
                <p>💡 <strong>Panduan Simulasi Direksi:</strong><br>Pilih salah satu nama pekerja di sebelah kiri untuk melihat rekomendasi jalur pemindahan kapabilitas (AHA Moment) secara otomatis.</p>
            </div>
        </div>
    </div>

    <script>
        const employees = [
            {
                id: "EMP-48213",
                name: "Budi Santoso",
                tenure: "14 Tahun (Senior)",
                currentRole: "Field Metering Specialist",
                region: "Unit Operasional Jawa Barat",
                aiRisk: "88% (High)",
                domainSkill: "Pemahaman Lapangan, Pemetaan Jaringan Lokal, Komunikasi Pelanggan",
                targetRole: "IoT Field Maintenance Specialist",
                matchRate: "85%",
                reskillTime: "4 Minggu (Blended OJT)",
                savings: "Rp 120 Juta / Pekerja"
            },
            {
                id: "EMP-39102",
                name: "Siti Rahmawati",
                tenure: "9 Tahun (Intermediate)",
                currentRole: "Senior Meter Reader II",
                region: "Unit Operasional Jawa Tengah",
                aiRisk: "82% (High)",
                domainSkill: "Akurasi Data Manual, Penanganan Komplain Warga",
                targetRole: "Digital Energy Advisor / Care Agent",
                matchRate: "88%",
                reskillTime: "3 Minggu (LMS & Online)",
                savings: "Rp 95 Juta / Pekerja"
            },
            {
                id: "EMP-51204",
                name: "Ahmad Hidayat",
                tenure: "18 Tahun (Senior Master)",
                currentRole: "Teknisi Pengawas Meteran",
                region: "Unit Operasional Jawa Timur",
                aiRisk: "75% (High)",
                domainSkill: "Supervisi Lapangan, Audit Fisik Jaringan, K3",
                targetRole: "Grid Asset Auditor & Team Supervisor",
                matchRate: "92%",
                reskillTime: "2 Minggu (Fast-Track)",
                savings: "Rp 140 Juta / Pekerja"
            }
        ];

        function renderEmployees() {
            const listContainer = document.getElementById('employeeList');
            listContainer.innerHTML = '';

            employees.forEach((emp, index) => {
                const card = document.createElement('div');
                card.className = `employee-card ${index === 0 ? 'active' : ''}`;
                card.onclick = () => selectEmployee(index);
                card.innerHTML = `
                    <div class="emp-info">
                        <h4>${emp.name}</h4>
                        <p>${emp.currentRole} • Masa Kerja: ${emp.tenure}</p>
                    </div>
                    <div class="emp-risk">
                        <span class="risk-tag risk-high">AI Disruption: ${emp.aiRisk}</span>
                    </div>
                `;
                listContainer.appendChild(card);
            });

            // Auto-select karyawan pertama saat awal dibuka
            selectEmployee(0);
        }

        function selectEmployee(index) {
            // Update active state card
            const cards = document.querySelectorAll('.employee-card');
            cards.forEach((card, i) => {
                card.classList.toggle('active', i === index);
            });

            const emp = employees[index];
            const detailPanel = document.getElementById('detailPanel');

            detailPanel.innerHTML = `
                <div class="panel-title">
                    <span>Profil Kapabilitas & Simulasi Redirection</span>
                    <span style="font-size: 11px; background: #e0e7ff; color: var(--primary); padding: 3px 8px; border-radius: 4px;">ID: ${emp.id}</span>
                </div>

                <div style="margin-bottom: 16px;">
                    <h3 style="font-size: 18px; color: var(--primary);">${emp.name}</h3>
                    <p style="font-size: 13px; color: var(--text-muted);">${emp.currentRole} — ${emp.region}</p>
                    <p style="font-size: 12px; margin-top: 6px;"><strong>Keahlian Saat Ini:</strong> ${emp.domainSkill}</p>
                </div>

                <!-- AHA MOMENT CARD -->
                <div class="aha-card">
                    <div class="aha-badge">Momen AHA! — Re-alignment</div>
                    <div class="aha-title">Rekomendasi Jabatan Baru (Capability Band)</div>
                    <div style="font-size: 16px; font-weight: 800; color: var(--text-main);">${emp.targetRole}</div>
                    
                    <div style="display: flex; align-items: center; gap: 16px; margin-top: 12px;">
                        <div>
                            <div style="font-size: 11px; color: var(--text-muted);">Pencocokan Kapabilitas</div>
                            <div class="match-score">${emp.matchRate}</div>
                        </div>
                        <div>
                            <div style="font-size: 11px; color: var(--text-muted);">Durasi Reskilling</div>
                            <div style="font-size: 18px; font-weight: 700; color: var(--primary); margin-top: 4px;">${emp.reskillTime}</div>
                        </div>
                    </div>

                    <div class="reskill-timeline">
                        <p><strong>Jalur Transisi Prioritas Senioritas:</strong> Prioritas Gelombang 1 (Selesai pada Day 60 Roadmap). Mencegah perekrutan vendor luar seharga ${emp.savings}.</p>
                    </div>
                </div>

                <button class="btn-action" onclick="alert('Rekomendasi Pemindahan Peran untuk ${emp.name} Berhasil Disimpan ke Sistem Dashboard Direksi!')">Disetujui untuk Program Reskilling (Day 60 Gate)</button>
            `;
        }

        // Jalankan saat dokumen selesai dimuat
        document.addEventListener('DOMContentLoaded', renderEmployees);
    </script>
</body>
</html>

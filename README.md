<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ใบเสนอราคา / QUOTATION</title>
    <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #1e3a8a;
            --primary-light: #eff6ff;
            --text-main: #1f2937;
            --border-color: #cbd5e1;
        }

        * {
            box-sizing: border-box;
            font-family: 'Sarabun', sans-serif;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: #f1f5f9;
            color: var(--text-main);
            padding: 15px;
            font-size: 12px;
        }

        .controls-panel {
            max-width: 850px;
            margin: 0 auto 15px auto;
            background: #ffffff;
            padding: 12px 18px;
            border-radius: 8px;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1);
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            align-items: center;
            justify-content: space-between;
        }

        .email-input-group {
            display: flex;
            align-items: center;
            gap: 8px;
            flex-grow: 1;
        }

        .email-input-group input {
            padding: 6px 10px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            width: 100%;
            max-width: 240px;
            font-size: 12px;
        }

        .btn {
            padding: 7px 12px;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            gap: 5px;
            font-size: 12px;
        }

        .btn-primary { background-color: var(--primary-color); color: white; }
        .btn-success { background-color: #059669; color: white; }
        .btn-info { background-color: #0284c7; color: white; }
        .btn-warning { background-color: #d97706; color: white; }

        /* Modal History Window */
        .modal-overlay {
            display: none;
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .modal-card {
            background: white;
            width: 90%;
            max-width: 600px;
            padding: 20px;
            border-radius: 8px;
            max-height: 80vh;
            overflow-y: auto;
        }

        .history-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: 1px solid var(--border-color);
        }

        /* Document Page Format */
        .page-container {
            max-width: 850px;
            margin: 0 auto;
            background: white;
            padding: 25px 30px;
            border-radius: 4px;
            box-shadow: 0 10px 15px -3px rgba(0,0,0,0.1);
        }

        .doc-header {
            display: flex;
            justify-content: space-between;
            border-bottom: 2px solid var(--primary-color);
            padding-bottom: 10px;
            margin-bottom: 12px;
        }

        .doc-header h1 { font-size: 18px; }
        .doc-header h2 { font-size: 18px; }

        .editable-field {
            border: 1px dashed transparent;
            padding: 1px 3px;
            border-radius: 4px;
            outline: none;
        }

        .editable-field:hover, .editable-field:focus {
            border-color: #94a3b8;
            background-color: #f8fafc;
        }

        .editable-field[data-placeholder]:empty:before {
            content: attr(data-placeholder);
            color: #94a3b8;
            font-style: italic;
        }

        .info-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 12px;
            background: var(--primary-light);
            padding: 10px 12px;
            border-radius: 6px;
            font-size: 11.5px;
        }

        /* Items Table Compact */
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 12px;
        }

        th {
            background-color: var(--primary-color);
            color: white;
            padding: 6px 8px;
            text-align: left;
            font-size: 11.5px;
        }

        td {
            border-bottom: 1px solid var(--border-color);
            padding: 4px 8px;
            font-size: 11px;
        }

        .text-center { text-align: center; }
        .text-right { text-align: right; }

        input.num-input {
            width: 100%;
            text-align: right;
            border: 1px solid var(--border-color);
            padding: 2px 4px;
            border-radius: 4px;
            font-size: 11px;
        }

        .summary-box {
            margin-left: auto;
            width: 300px;
            margin-bottom: 10px;
            font-size: 11.5px;
        }

        .summary-row {
            display: flex;
            justify-content: space-between;
            padding: 3px 0;
            border-bottom: 1px solid #e2e8f0;
        }

        .grand-total {
            font-weight: 700;
            color: var(--primary-color);
            font-size: 13px;
            border-bottom: 2px solid var(--primary-color);
        }

        .thai-bath-text {
            background: #f8fafc;
            padding: 6px 10px;
            border-radius: 4px;
            font-weight: 600;
            margin-bottom: 12px;
            border-left: 3px solid var(--primary-color);
            font-size: 11.5px;
        }

        .payment-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 15px;
            padding: 8px 12px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            background-color: #fafafa;
        }

        .payment-title {
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 4px;
            font-size: 11.5px;
        }

        .payment-details p {
            font-size: 11px;
            line-height: 1.4;
        }

        .signatures {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            text-align: center;
            font-size: 11px;
        }

        .sig-box { width: 42%; }
        .sig-line { border-bottom: 1px dashed #000; margin: 25px 0 6px 0; }

        @media print {
            @page {
                size: A4 portrait;
                margin: 8mm 10mm;
            }
            html, body {
                height: 100%;
                background: white;
                padding: 0;
                font-size: 11px;
            }
            .controls-panel, .modal-overlay { display: none !important; }
            .page-container {
                box-shadow: none;
                padding: 0;
                width: 100%;
                max-width: 100%;
            }
            input.num-input {
                border: none;
                background: transparent;
            }
            tr.empty-row {
                display: none !important;
            }
            .doc-header h1, .doc-header h2 { font-size: 16px; }
            .signatures { margin-top: 15px; }
            .sig-line { margin: 20px 0 5px 0; }
        }
    </style>
</head>
<body>

    <div class="controls-panel">
        <div class="email-input-group">
            <label for="clientEmail"><strong>อีเมลผู้รับ:</strong></label>
            <input type="email" id="clientEmail" placeholder="ระบุอีเมลลูกค้าสำหรับส่งข้อมูล">
        </div>
        <div style="display: flex; gap: 6px;">
            <button class="btn btn-warning" onclick="saveDocument()">💾 บันทึก</button>
            <button class="btn btn-info" onclick="openHistoryModal()">📂 ประวัติเอกสาร</button>
            <button class="btn btn-success" onclick="sendEmail()">📧 ส่งเมล</button>
            <button class="btn btn-primary" onclick="window.print()">🖨️ พิมพ์ A4</button>
        </div>
    </div>

    <!-- Modal แสดงประวัติเอกสาร -->
    <div class="modal-overlay" id="historyModal">
        <div class="modal-card">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
                <h3 style="color: var(--primary-color);">📂 รายการใบเสนอราคาที่บันทึกไว้</h3>
                <button class="btn" onclick="closeHistoryModal()">❌ ปิด</button>
            </div>
            <div id="historyList">
                <p style="text-align: center; color: #64748b;">ไม่มีข้อมูลเอกสารที่บันทึกไว้</p>
            </div>
        </div>
    </div>

    <div class="page-container">
        <div class="doc-header">
            <div>
                <h1 style="color: var(--primary-color);" class="editable-field" contenteditable="true" id="companyName" data-placeholder="ระบุชื่อบริษัท/ผู้รับจ้าง"></h1>
                <p class="editable-field" contenteditable="true" id="companyAddress" data-placeholder="ระบุที่อยู่ผู้รับจ้าง"></p>
                <p>โทร: <span class="editable-field" contenteditable="true" id="companyPhone">081-234-5678</span> | LINE ID / Email: <span class="editable-field" contenteditable="true" id="companyLine">ID ศณ์ฎ</span></p>
            </div>
            <div style="text-align: right;">
                <h2 style="color: var(--primary-color);">ใบเสนอราคา</h2>
                <p style="font-size: 12px; color: #64748b;">QUOTATION</p>
                <p style="margin-top: 5px;"><strong>เลขที่:</strong> <span class="editable-field" contenteditable="true" id="docNumber">QT-20261010-001</span></p>
                <p><strong>วันที่:</strong> <span class="editable-field" contenteditable="true" id="docDate">10 ตุลาคม 2569</span></p>
            </div>
        </div>

        <div class="info-grid">
            <div>
                <strong>ข้อมูลลูกค้า / ผู้ว่าจ้าง:</strong>
                <p class="editable-field" contenteditable="true" id="clientName" data-placeholder="ระบุชื่อลูกค้า/บ้านเลขที่"></p>
                <p class="editable-field" contenteditable="true" id="clientAddress" data-placeholder="ระบุสถานที่ซ่อม"></p>
            </div>
            <div>
                <strong>เงื่อนไขโครงการ:</strong>
                <p>กำหนดยืนราคา: <span class="editable-field" contenteditable="true" id="validDays">30 วัน</span></p>
                <p>ระยะเวลาซ่อมแซม: <span class="editable-field" contenteditable="true" id="repairDays" data-placeholder="ระบุจำนวนวัน"></span> วันทำการ</p>
            </div>
        </div>

        <table>
            <thead>
                <tr>
                    <th style="width: 6%;">ข้อ</th>
                    <th style="width: 52%;">รายการงานซ่อมแซม</th>
                    <th style="width: 10%;" class="text-center">จำนวน</th>
                    <th style="width: 10%;" class="text-center">หน่วย</th>
                    <th style="width: 11%;" class="text-right">ราคา/หน่วย</th>
                    <th style="width: 11%;" class="text-right">จำนวนเงิน (บาท)</th>
                </tr>
            </thead>
            <tbody id="itemsBody">
                <!-- 14 Rows generated automatically via JS -->
            </tbody>
        </table>

        <div class="summary-box">
            <div class="summary-row">
                <span>รวมราคาทั้งสิ้น (Subtotal):</span>
                <span id="subtotal">0.00</span>
            </div>
            <div class="summary-row">
                <span>ภาษีมูลค่าเพิ่ม VAT 7%:</span>
                <span id="vat">0.00</span>
            </div>
            <div class="summary-row grand-total">
                <span>จำนวนเงินสุทธิ (Grand Total):</span>
                <span id="grandTotal">0.00</span>
            </div>
        </div>

        <div class="thai-bath-text">
            จำนวนเงินสุทธิ (ตัวอักษร): <span id="thaiBathText">-ศูนย์บาทถ้วน-</span>
        </div>

        <div class="payment-section">
            <div class="payment-details">
                <div class="payment-title">📌 เงื่อนไขการชำระเงิน (Payment Terms)</div>
                <p class="editable-field" contenteditable="true" id="payTerm1">1. งวดที่ 1: มัดจำ 50% ณ วันตกลงทำสัญญาว่าจ้าง</p>
                <p class="editable-field" contenteditable="true" id="payTerm2">2. งวดที่ 2: ชำระส่วนที่เหลือ 50% เมื่อส่งมอบงานเสร็จสิ้น</p>
            </div>
            <div class="payment-details">
                <div class="payment-title">🏦 ช่องทางการชำระเงิน / เลขที่บัญชี</div>
                <p>ธนาคาร: <span class="editable-field" contenteditable="true" id="bankName">กสิกรไทย (KBANK)</span></p>
                <p>เลขที่บัญชี: <strong class="editable-field" contenteditable="true" id="bankAcc">123-4-56789-0</strong></p>
                <p>ชื่อบัญชี: <span class="editable-field" contenteditable="true" id="bankOwner">บริษัท ช่างซ่อมบ้านมืออาชีพ จำกัด</span></p>
                <p>สาขา: <span class="editable-field" contenteditable="true" id="bankBranch">สุขุมวิท</span></p>
            </div>
        </div>

        <div class="signatures">
            <div class="sig-box">
                <p>ลงชื่อ..........................................................</p>
                <div class="sig-line"></div>
                <p>( ผู้เสนอราคา / ช่างผู้ดูแล )</p>
            </div>
            <div class="sig-box">
                <p>ลงชื่อ..........................................................</p>
                <div class="sig-line"></div>
                <p>( ผู้สั่งซื้อ / ผู้ว่าจ้าง )</p>
            </div>
        </div>
    </div>

    <script>
        // Auto Set Today's Date and Auto Document Number
        function initAutoDateAndDocNo() {
            const now = new Date();
            const thaiMonths = [
                "มกราคม", "กุมภาพันธ์", "มีนาคม", "เมษายน", "พฤษภาคม", "มิถุนายน",
                "กรกฎาคม", "สิงหาคม", "กันยายน", "ตุลาคม", "พฤศจิกายน", "ธันวาคม"
            ];
            
            const day = now.getDate();
            const monthStr = thaiMonths[now.getMonth()];
            const thaiYear = now.getFullYear() + 543;
            
            document.getElementById('docDate').textContent = `${day} ${monthStr} ${thaiYear}`;

            const yyyy = now.getFullYear();
            const mm = String(now.getMonth() + 1).padStart(2, '0');
            const dd = String(now.getDate()).padStart(2, '0');
            document.getElementById('docNumber').textContent = `QT-${yyyy}${mm}${dd}-001`;
        }

        // Render 14 Rows
        const tbody = document.getElementById('itemsBody');
        for (let idx = 0; idx < 14; idx++) {
            const tr = document.createElement('tr');
            tr.innerHTML = `
                <td class="text-center item-no">${idx + 1}</td>
                <td contenteditable="true" class="editable-field item-title" data-placeholder="ระบุรายการงานซ่อม..." oninput="calculateTotals()"></td>
                <td><input type="number" class="num-input qty" value="1" min="0" oninput="calculateTotals()"></td>
                <td contenteditable="true" class="text-center editable-field item-unit">งาน</td>
                <td><input type="number" class="num-input price" value="0" min="0" oninput="calculateTotals()"></td>
                <td class="text-right total-cell">0.00</td>
            `;
            tbody.appendChild(tr);
        }

        // Thai Baht Text Conversion Algorithm
        function ArabicToThaiBaht(numbers) {
            numbers = Number(numbers).toFixed(2);
            if (numbers == 0) return "-ศูนย์บาทถ้วน-";
            
            const numberTxt = ["ศูนย์", "หนึ่ง", "สอง", "สาม", "สี่", "ห้า", "หก", "เจ็ด", "แปด", "เก้า"];
            const unitTxt = ["", "สิบ", "ร้อย", "พัน", "หมื่น", "แสน", "ล้าน"];
            
            let [baht, satang] = numbers.split('.');
            let bahtStr = "";
            
            for (let i = 0; i < baht.length; i++) {
                let digit = parseInt(baht.charAt(i));
                let pos = baht.length - i - 1;
                if (digit !== 0) {
                    if (pos === 1 && digit === 1) bahtStr += "สิบ";
                    else if (pos === 1 && digit === 2) bahtStr += "ยี่สิบ";
                    else if (pos === 0 && digit === 1 && baht.length > 1) bahtStr += "เอ็ด";
                    else bahtStr += numberTxt[digit] + unitTxt[pos % 6];
                }
            }
            bahtStr += "บาท";

            if (parseInt(satang) === 0) {
                bahtStr += "ถ้วน";
            } else {
                for (let i = 0; i < satang.length; i++) {
                    let digit = parseInt(satang.charAt(i));
                    let pos = satang.length - i - 1;
                    if (digit !== 0) {
                        if (pos === 1 && digit === 1) bahtStr += "สิบ";
                        else if (pos === 1 && digit === 2) bahtStr += "ยี่สิบ";
                        else if (pos === 0 && digit === 1) bahtStr += "เอ็ด";
                        else bahtStr += numberTxt[digit] + (pos === 1 ? "สิบ" : "");
                    }
                }
                bahtStr += "สตางค์";
            }
            return "-" + bahtStr + "-";
        }

        // Auto Calculation Function
        function calculateTotals() {
            let subtotal = 0;
            const rows = document.querySelectorAll('#itemsBody tr');
            
            rows.forEach(row => {
                const title = row.querySelector('.item-title').textContent.trim();
                const qty = parseFloat(row.querySelector('.qty').value) || 0;
                const price = parseFloat(row.querySelector('.price').value) || 0;
                const lineTotal = qty * price;
                
                row.querySelector('.total-cell').textContent = lineTotal.toLocaleString('th-TH', {minimumFractionDigits: 2, maximumFractionDigits: 2});
                subtotal += lineTotal;

                if (!title || price === 0 || qty === 0) {
                    row.classList.add('empty-row');
                } else {
                    row.classList.remove('empty-row');
                }
            });

            const vat = subtotal * 0.07;
            const grandTotal = subtotal + vat;

            document.getElementById('subtotal').textContent = subtotal.toLocaleString('th-TH', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('vat').textContent = vat.toLocaleString('th-TH', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('grandTotal').textContent = grandTotal.toLocaleString('th-TH', {minimumFractionDigits: 2, maximumFractionDigits: 2});

            document.getElementById('thaiBathText').textContent = ArabicToThaiBaht(grandTotal);
        }

        // Storage & History Management
        function saveDocument() {
            const docNo = document.getElementById('docNumber').textContent.trim();
            if (!docNo) {
                alert('กรุณาระบุเลขที่เอกสารครับ');
                return;
            }

            const items = [];
            document.querySelectorAll('#itemsBody tr').forEach(row => {
                items.push({
                    title: row.querySelector('.item-title').textContent.trim(),
                    qty: row.querySelector('.qty').value,
                    unit: row.querySelector('.item-unit').textContent.trim(),
                    price: row.querySelector('.price').value
                });
            });

            const docData = {
                docNo: docNo,
                docDate: document.getElementById('docDate').textContent.trim(),
                companyName: document.getElementById('companyName').textContent.trim(),
                companyAddress: document.getElementById('companyAddress').textContent.trim(),
                companyPhone: document.getElementById('companyPhone').textContent.trim(),
                companyLine: document.getElementById('companyLine').textContent.trim(),
                clientName: document.getElementById('clientName').textContent.trim(),
                clientAddress: document.getElementById('clientAddress').textContent.trim(),
                clientEmail: document.getElementById('clientEmail').value,
                grandTotal: document.getElementById('grandTotal').textContent,
                items: items,
                savedAt: new Date().toLocaleString('th-TH')
            };

            let savedList = JSON.parse(localStorage.getItem('quotationsList') || '{}');
            savedList[docNo] = docData;
            localStorage.setItem('quotationsList', JSON.stringify(savedList));

            alert(`บันทึกเอกสารเลขที่ ${docNo} สำเร็จเรียบร้อยครับ!`);
        }

        function openHistoryModal() {
            const modal = document.getElementById('historyModal');
            const historyList = document.getElementById('historyList');
            const savedList = JSON.parse(localStorage.getItem('quotationsList') || '{}');

            const keys = Object.keys(savedList);
            if (keys.length === 0) {
                historyList.innerHTML = '<p style="text-align: center; color: #64748b; padding: 20px;">ไม่มีข้อมูลเอกสารที่บันทึกไว้</p>';
            } else {
                let html = '';
                keys.reverse().forEach(key => {
                    const doc = savedList[key];
                    html += `
                        <div class="history-item">
                            <div>
                                <strong>${doc.docNo}</strong> - ${doc.clientName || 'ไม่ระบุชื่อลูกค้า'}<br>
                                <small style="color: #64748b;">วันที่: ${doc.docDate} | ยอดรวม: ${doc.grandTotal} บาท</small>
                            </div>
                            <div style="display: flex; gap: 5px;">
                                <button class="btn btn-info" onclick="loadDocument('${doc.docNo}')">📂 ดึงข้อมูล</button>
                                <button class="btn btn-warning" onclick="deleteDocument('${doc.docNo}')">🗑️ ลบ</button>
                            </div>
                        </div>
                    `;
                });
                historyList.innerHTML = html;
            }
            modal.style.display = 'flex';
        }

        function closeHistoryModal() {
            document.getElementById('historyModal').style.display = 'none';
        }

        function loadDocument(docNo) {
            const savedList = JSON.parse(localStorage.getItem('quotationsList') || '{}');
            const doc = savedList[docNo];
            if (!doc) return;

            document.getElementById('docNumber').textContent = doc.docNo;
            document.getElementById('docDate').textContent = doc.docDate;
            document.getElementById('companyName').textContent = doc.companyName;
            document.getElementById('companyAddress').textContent = doc.companyAddress;
            document.getElementById('companyPhone').textContent = doc.companyPhone;
            document.getElementById('companyLine').textContent = doc.companyLine;
            document.getElementById('clientName').textContent = doc.clientName;
            document.getElementById('clientAddress').textContent = doc.clientAddress;
            document.getElementById('clientEmail').value = doc.clientEmail || '';

            const rows = document.querySelectorAll('#itemsBody tr');
            doc.items.forEach((item, idx) => {
                if (rows[idx]) {
                    rows[idx].querySelector('.item-title').textContent = item.title;
                    rows[idx].querySelector('.qty').value = item.qty;
                    rows[idx].querySelector('.item-unit').textContent = item.unit;
                    rows[idx].querySelector('.price').value = item.price;
                }
            });

            calculateTotals();
            closeHistoryModal();
            alert(`ดึงข้อมูลเอกสาร ${docNo} เรียบร้อยแล้วครับ!`);
        }

        function deleteDocument(docNo) {
            if (confirm(`คุณต้องการลบเอกสารเลขที่ ${docNo} ใช่หรือไม่?`)) {
                let savedList = JSON.parse(localStorage.getItem('quotationsList') || '{}');
                delete savedList[docNo];
                localStorage.setItem('quotationsList', JSON.stringify(savedList));
                openHistoryModal();
            }
        }

        // Email Trigger Function
        function sendEmail() {
            const email = document.getElementById('clientEmail').value;
            if (!email) {
                alert('กรุณากรอกอีเมลผู้รับก่อนส่งข้อความครับ');
                return;
            }

            let itemListText = "";
            let itemIndex = 1;
            const rows = document.querySelectorAll('#itemsBody tr');

            rows.forEach(row => {
                const title = row.querySelector('.item-title').textContent.trim();
                const qty = parseFloat(row.querySelector('.qty').value) || 0;
                const unit = row.querySelector('.item-unit').textContent.trim();
                const price = parseFloat(row.querySelector('.price').value) || 0;
                const lineTotal = qty * price;

                if (title && price > 0 && qty > 0) {
                    itemListText += `${itemIndex}. ${title} - ${qty} ${unit} x ${price.toLocaleString()} = ${lineTotal.toLocaleString()} บาท\n`;
                    itemIndex++;
                }
            });

            const docNo = document.getElementById('docNumber').textContent;
            const grandTotal = document.getElementById('grandTotal').textContent;
            const thaiText = document.getElementById('thaiBathText').textContent;
            const bankName = document.getElementById('bankName').textContent;
            const bankAcc = document.getElementById('bankAcc').textContent;
            const bankOwner = document.getElementById('bankOwner').textContent;
            
            const subject = encodeURIComponent(`ใบเสนอราคางานซ่อมแซมบ้าน เลขที่ ${docNo}`);
            const body = encodeURIComponent(`เรียน คุณลูกค้า,\n\nทางเราขอส่งสรุปใบเสนอราคาสำหรับงานซ่อมแซมบ้าน\n\n[ รายการงานซ่อมแซม ]\n${itemListText}\nยอดรวมสุทธิทั้งสิ้น (รวม VAT): ${grandTotal} บาท (${thaiText})\n\n[ ช่องทางการชำระเงิน ]\nธนาคาร: ${bankName}\nเลขที่บัญชี: ${bankAcc}\nชื่อบัญชี: ${bankOwner}\n\nรายละเอียดรายการตามเอกสารใบเสนอราคาแนบ\n\nขอบคุณครับ`);
            
            window.location.href = `mailto:${email}?subject=${subject}&body=${body}`;
        }

        // Run Initializers
        initAutoDateAndDocNo();
        calculateTotals();
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ứng dụng Quản lý Thôn Xóm - Làng Số</title>
    
    <!-- Cấu hình để điện thoại nhận diện đây là một Ứng dụng có thể cài đặt -->
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="apple-mobile-web-app-title" content="Làng Số">
    
    <!-- Nhúng trực tiếp file Manifest cấu hình cài đặt cho Android/iOS -->
    <link rel="manifest" href="data:application/manifest+json;base64,ewogICAgIm5hbWUiOiAiS2h1IERhbiBDxrAgTMOgbmcsIFPhu5EiLAogICAgInNob3J0X25hbWUiOiAiTMGgbmcsIFPhu5EiLAogICAgInN0YXJ0X3VybCI6ICIuIiwKICAgICJkaXNwbGF5IjogInN0YW5kYWxvbmUiLAogICAgImJhY2tncm91bmRfY29sb3IiOiAiI2Y0ZjZmOCIsCiAgICAidGhlbWVfY29sb3IiOiAiIzJlN2QzMiIsCiAgICAiaWNvbnMiOiBbCiAgICAgICAgewogICAgICAgICAgICAic3JjIjogImRhdGE6aW1hZ2Uvc3ZnK3htbCw8c3ZnIHhtbG5zPSdodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2Zycgdmlld0JveD0nMCAwIDEwMCAxMDAnPjxyZWN0IHdpZHRoPScxMDAnIGhlaWdodD0nMTAwJyByeD0nMjAnIGZpbGw9JyMyZTdkMzInLz48dGV4dCB4PSc1MCUnIHk9JzY1JScgZm9udC1zaXplPSc0NScgZm9udC13ZWlnaHQ9J2JvbGQnIGZpbGw9J3doaXRlJyB0ZXh0LWFuY2hvcj0nbWlkZGxlJz7TMSA8L3RleHQ+PC9zdmc+IiwKICAgICAgICAgICAgInNpemVzIjogIjUxMng1MTIiLAogICAgICAgICAgICAidHlwZSI6ICJpbWFnZS9zdmcreG1sIgogICAgICAgIH0KICAgIF0KfQ==">

    <style>
        :root {
            --primary-color: #2e7d32;
            --secondary-color: #1565c0;
            --background-color: #f4f6f8;
            --card-color: #ffffff;
            --text-color: #212121;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--background-color);
            color: var(--text-color);
            margin: 0;
            padding: 0;
        }

        header {
            background-color: var(--primary-color);
            color: white;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        header h1 { margin: 0; font-size: 28px; }
        header p { margin: 5px 0 0 0; font-size: 16px; opacity: 0.9; }

        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 0 15px;
        }

        /* Nút cài đặt ứng dụng nhanh */
        #pwa-install-banner {
            display: none;
            background: #fff3e0;
            border: 2px dashed #ff9800;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            text-align: center;
        }

        /* Thanh điều hướng tab */
        .tabs {
            display: flex;
            background: #e0e0e0;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
        }

        .tab-btn {
            flex: 1;
            padding: 15px;
            border: none;
            background: none;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
            color: #555;
        }

        .tab-btn.active {
            background-color: var(--secondary-color);
            color: white;
        }

        .tab-content {
            display: none;
            background: var(--card-color);
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }

        .tab-content.active { display: block; }

        h2 { color: var(--primary-color); margin-top: 0; font-size: 22px; border-bottom: 2px solid #eee; padding-bottom: 10px; }
        label { display: block; font-weight: bold; margin: 15px 0 5px 0; font-size: 18px; }
        
        textarea, input, select {
            width: 100%;
            padding: 12px;
            font-size: 18px;
            border: 2px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
            margin-bottom: 10px;
        }

        textarea { height: 120px; resize: vertical; }

        button.btn-main {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 15px 20px;
            font-size: 18px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            width: 100%;
            transition: 0.2s;
            box-shadow: 0 3px 5px rgba(0,0,0,0.2);
        }

        button.btn-main:hover { opacity: 0.9; }
        button.btn-secondary { background-color: #e65100; margin-top: 5px; }

        .list-item {
            background: #f9f9f9;
            border-left: 5px solid var(--primary-color);
            padding: 15px;
            margin-top: 15px;
            border-radius: 4px;
        }
        .list-item h4 { margin: 0 0 5px 0; font-size: 18px; color: #333; }
        .list-item p { margin: 0; color: #666; font-size: 16px; }

        .poll-bar-bg { background: #eee; border-radius: 8px; height: 25px; margin-top: 8px; overflow: hidden; }
        .poll-bar-fill { background: var(--secondary-color); height: 100%; width: 0%; transition: width 0.5s; }
    </style>
</head>
<body>

    <header>
        <h1>BẢNG ĐIỀU HÀNH THÔN XÓM - LÀNG SỐ</h1>
        <p>Giao diện điều hành thôn xóm & tương tác trực tuyến cho người dân</p>
    </header>

    <div class="container">
        
        <!-- Biển báo nhắc người dân cài đặt nhanh ứng dụng nếu điện thoại hỗ trợ -->
        <div id="pwa-install-banner">
            <p style="margin:0 0 10px 0; font-size:16px; font-weight:bold; color:#e65100;">📲 Bấm vào đây để cài đặt Ứng dụng "Làng Số" ra màn hình điện thoại của bạn!</p>
            <button class="btn-main" id="btn-pwa-install" style="padding: 10px; font-size: 16px;">TẢI VỀ VÀ CÀI ĐẶT NGAY</button>
        </div>

        <div class="tabs">
            <button class="tab-btn active" onclick="openTab('loa')">📢 Loa Phát Thanh AI</button>
            <button class="tab-btn" onclick="openTab('quy')">💰 Quỹ & Thu Chi</button>
            <button class="tab-btn" onclick="openTab('bieuquet')">🗳️ Biểu Quyết</button>
        </div>

        <!-- TAB 1: LOA PHÁT THANH AI -->
        <div id="loa" class="tab-content active">
            <h2>📢 Trình phát thông báo AI ra hệ thống loa xóm</h2>
            <label for="thongbao-text">Nhập nội dung thông báo cho bà con:</label>
            <textarea id="thongbao-text" placeholder="Ví dụ: Kính thưa toàn thể bà con trong xóm, tối nay 19 giờ 30 phút mời đại diện các hộ gia đình ra nhà văn hóa họp xóm..."></textarea>
            
            <label for="voice-select">Chọn giọng đọc AI:</label>
            <select id="voice-select">
                <option value="vi-VN">Giọng nói Tiếng Việt Tiêu Chuẩn</option>
            </select>

            <button class="btn-main" onclick="phatLoaAI()">⚡ PHÁT LOA THÔNG BÁO NGAY</button>
            <button class="btn-main btn-secondary" onclick="dungPhatLoa()">🛑 DỪNG PHÁT LOA KHẨN CẤP</button>

            <h3 style="margin-top:25px;">📋 Nhật ký thông báo đã phát gần đây:</h3>
            <div id="log-thongbao">
                <div class="list-item">
                    <h4>Thông báo tiêm chủng mở rộng</h4>
                    <p>Đã phát lúc 08:00 sáng nay • Người nghe: Toàn xóm</p>
                </div>
            </div>
        </div>

        <!-- TAB 2: QUẢN LÝ QUỸ THU CHI -->
        <div id="quy" class="tab-content">
            <h2>💰 Sổ tay quản lý quỹ xóm & Tạo mã đóng góp trực tuyến</h2>
            <div style="background: #e8f5e9; padding: 15px; border-radius: 8px; margin-bottom: 20px; font-size: 18px;">
                💸 <strong>Số dư Quỹ xóm hiện tại:</strong> <span style="color:#2e7d32; font-weight:bold; font-size: 22px;">15.450.000 đ</span>
            </div>
            <h3>Tạo đợt thu quỹ mới (Tự động sinh QR đóng tiền cho dân)</h3>
            <label>Tên khoản thu:</label>
            <input type="text" id="ten-khoan-thu" placeholder="Ví dụ: Tiền điện đường Trung thu">
            <label>Số tiền mỗi hộ cần đóng (đ):</label>
            <input type="number" id="so-tien-thu" placeholder="Ví dụ: 50000">
            <button class="btn-main" onclick="taoKhoanThu()">📌 PHÁT ĐỘNG THU QUỸ & XUẤT MÃ QR</button>

            <h3 style="margin-top:25px;">👥 Trạng thái nộp quỹ các hộ:</h3>
            <div id="danh-sach-thu">
                <div class="list-item" style="border-left-color: #e65100;">
                    <h4>Đang thu: Tiền quỹ khuyến học năm học mới</h4>
                    <p>Tiến độ: <strong>32 / 45 hộ</strong> đã đóng (Đạt 71%)</p>
                </div>
            </div>
        </div>

        <!-- TAB 3: BIỂU QUYẾT SỐ -->
        <div id="bieuquet" class="tab-content">
            <h2>🗳️ Lấy ý kiến biểu quyết của nhân dân từ xa</h2>
            <label>Nội dung cần lấy ý kiến bà con:</label>
            <textarea id="noidung-vote" placeholder="Ví dụ: Xóm ta có nên đóng góp thêm mỗi hộ 100.000đ để lắp thêm 3 camera an ninh ở ngã tư không?"></textarea>
            <button class="btn-main" onclick="taoBieuQuyet()">🚀 MỞ CUỘC BIỂU QUYẾT SỐ</button>

            <h3 style="margin-top:25px;">📊 Kết quả các cuộc biểu quyết đang diễn ra:</h3>
            <div id="danh-sach-vote">
                <div class="list-item">
                    <h4>Vấn đề: Đổi giờ đổ rác mùa hè sang 18h30</h4>
                    <p>👍 Đồng ý: 85% (38 hộ) | 👎 Không đồng ý: 15% (7 hộ)</p>
                    <div class="poll-bar-bg"><div class="poll-bar-fill" style="width: 85%;"></div></div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Hàm chuyển đổi tab
        function openTab(tabId) {
            let contents = document.getElementsByClassName('tab-content');
            for (let i = 0; i < contents.length; i++) contents[i].classList.remove('active');

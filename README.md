<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HỆ THỐNG BÁO CÁO SALES & KPI FRAMEWORK - MONTSAND</title>
    <style>
        @media print {
            body { margin: 0; padding: 20mm; }
            .page-break { page-break-before: always; }
            .no-print { display: none; }
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background: #f8f9fa;
        }
        
        .container {
            background: white;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }
        
        h1 {
            color: #2c3e50;
            text-align: center;
            border-bottom: 3px solid #3498db;
            padding-bottom: 20px;
            margin-bottom: 30px;
            font-size: 2.2em;
        }
        
        h2 {
            color: #34495e;
            margin-top: 40px;
            margin-bottom: 20px;
            padding-left: 15px;
            border-left: 5px solid #3498db;
            font-size: 1.5em;
        }
        
        h3 {
            color: #2c3e50;
            margin-top: 30px;
            margin-bottom: 15px;
            font-size: 1.3em;
        }
        
        h4 {
            color: #34495e;
            margin-top: 25px;
            margin-bottom: 12px;
            font-size: 1.1em;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            font-size: 14px;
        }
        
        th, td {
            border: 1px solid #ddd;
            padding: 12px 8px;
            text-align: left;
        }
        
        th {
            background-color: #3498db;
            color: white;
            font-weight: bold;
        }
        
        tr:nth-child(even) {
            background-color: #f8f9fa;
        }
        
        .status-excellent { color: #27ae60; font-weight: bold; }
        .status-good { color: #f39c12; font-weight: bold; }
        .status-average { color: #e74c3c; font-weight: bold; }
        
        .metric-box {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
            text-align: center;
        }
        
        .metric-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 20px 0;
        }
        
        .metric-card {
            background: white;
            border: 2px solid #e8e8e8;
            border-radius: 8px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        
        .metric-value {
            font-size: 2em;
            font-weight: bold;
            color: #3498db;
            margin: 10px 0;
        }
        
        .metric-label {
            color: #7f8c8d;
            font-size: 0.9em;
            margin-bottom: 5px;
        }
        
        .warning-box {
            background: #fff3cd;
            border: 1px solid #ffeaa7;
            border-radius: 5px;
            padding: 15px;
            margin: 20px 0;
        }
        
        .alert-box {
            background: #f8d7da;
            border: 1px solid #f5c6cb;
            border-radius: 5px;
            padding: 15px;
            margin: 20px 0;
        }
        
        .success-box {
            background: #d1edff;
            border: 1px solid #74b9ff;
            border-radius: 5px;
            padding: 15px;
            margin: 20px 0;
        }
        
        .checklist {
            background: #f8f9fa;
            border-left: 4px solid #28a745;
            padding: 20px;
            margin: 20px 0;
        }
        
        .checklist ul {
            list-style-type: none;
            padding-left: 0;
        }
        
        .checklist li {
            margin: 10px 0;
            padding-left: 30px;
            position: relative;
        }
        
        .checklist li:before {
            content: "☐";
            position: absolute;
            left: 0;
            color: #28a745;
            font-size: 1.2em;
        }
        
        .toc {
            background: #f8f9fa;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            padding: 20px;
            margin: 30px 0;
        }
        
        .toc h3 {
            color: #495057;
            margin-top: 0;
        }
        
        .toc ul {
            list-style-type: decimal;
        }
        
        .toc a {
            color: #007bff;
            text-decoration: none;
        }
        
        .toc a:hover {
            text-decoration: underline;
        }
        
        .print-button {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #007bff;
            color: white;
            border: none;
            padding: 12px 24px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            z-index: 1000;
        }
        
        .print-button:hover {
            background: #0056b3;
        }
        
        @media (max-width: 768px) {
            .container { padding: 20px; }
            .metric-grid { grid-template-columns: 1fr; }
            h1 { font-size: 1.8em; }
        }
    </style>
</head>
<body>
    <button class="print-button no-print" onclick="window.print()">📄 In PDF</button>
    
    <div class="container">
        <h1>HỆ THỐNG BÁO CÁO BÁN HÀNG & KHUNG CHỈ TIÊU KPI</h1>
        <div class="metric-box">
            <h2 style="margin: 0; color: white;">Hệ Thống Quản Lý Hiệu Suất Bán Hàng MONTSAND</h2>
        </div>
        
        <div class="toc">
            <h3>📋 MỤC LỤC</h3>
            <ul>
                <li><a href="#structure">Cấu Trúc Báo Cáo Bán Hàng Tổng Thể</a></li>
                <li><a href="#kpi-framework">Khung Chỉ Tiêu KPI</a></li>
                <li><a href="#alerts">Cảnh Báo & Hành Động Tự Động</a></li>
                <li><a href="#implementation">Checklist Triển Khai</a></li>
            </ul>
        </div>

        <div class="page-break"></div>
        
        <section id="structure">
            <h2>📊 CẤU TRÚC BÁO CÁO BÁN HÀNG TỔNG THỂ</h2>
            
            <h3>📈 CẤP 1: BẢNG ĐIỀU KHIỂN ĐIỀU HÀNH - BÁO CÁO TỔNG QUAN LÃNH ĐẠO</h3>
            <p><strong>Tần suất:</strong> Cập nhật hàng ngày, báo cáo hàng tuần</p>
            
            <h4>A. Bảng Điểm Tổng Quan Bán Hàng</h4>
            <table>
                <thead>
                    <tr>
                        <th>Chỉ Số Chính</th>
                        <th>Thực Tế</th>
                        <th>Mục Tiêu</th>
                        <th>Năm Trước</th>
                        <th>Chênh Lệch</th>
                        <th>Xu Hướng</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Doanh Thu Tháng</strong></td>
                        <td>9,8 tỷ VNĐ</td>
                        <td>10,4 tỷ VNĐ</td>
                        <td>8,8 tỷ VNĐ</td>
                        <td class="status-average">-5,6% ↓</td>
                        <td class="status-excellent">+11,8% YoY ↑</td>
                    </tr>
                    <tr>
                        <td><strong>Doanh Thu Bình Quân/Ngày</strong></td>
                        <td>328 triệu VNĐ</td>
                        <td>347 triệu VNĐ</td>
                        <td>294 triệu VNĐ</td>
                        <td class="status-average">-5,3% ↓</td>
                        <td class="status-excellent">+11,8% YoY ↑</td>
                    </tr>
                    <tr>
                        <td><strong>Số Lượng Đơn Hàng</strong></td>
                        <td>1.247</td>
                        <td>1.350</td>
                        <td>1.150</td>
                        <td class="status-average">-7,6% ↓</td>
                        <td class="status-excellent">+8,4% YoY ↑</td>
                    </tr>
                    <tr>
                        <td><strong>Giá Trị Đơn Hàng TB</strong></td>
                        <td>7,87 triệu VNĐ</td>
                        <td>7,70 triệu VNĐ</td>
                        <td>7,64 triệu VNĐ</td>
                        <td class="status-excellent">+2,4% ↑</td>
                        <td class="status-excellent">+3,3% YoY ↑</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Chuyển Đổi</strong></td>
                        <td>2,8%</td>
                        <td>3,2%</td>
                        <td>2,6%</td>
                        <td class="status-average">-12,5% ↓</td>
                        <td class="status-excellent">+7,7% YoY ↑</td>
                    </tr>
                </tbody>
            </table>

            <h4>B. Ma Trận Hiệu Suất Kênh Bán Hàng</h4>
            <table>
                <thead>
                    <tr>
                        <th>Kênh Bán Hàng</th>
                        <th>Doanh Thu</th>
                        <th>% Tỷ Trọng</th>
                        <th>Tăng Trưởng</th>
                        <th>Trạng Thái</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Website Trực Tiếp</strong></td>
                        <td>4,42 tỷ VNĐ</td>
                        <td>45%</td>
                        <td>+15,2%</td>
                        <td class="status-excellent">🟢 Xuất Sắc</td>
                    </tr>
                    <tr>
                        <td><strong>CULT MIA</strong></td>
                        <td>1,96 tỷ VNĐ</td>
                        <td>20%</td>
                        <td>+8,7%</td>
                        <td class="status-good">🟡 Tốt</td>
                    </tr>
                    <tr>
                        <td><strong>MEAN BLVD</strong></td>
                        <td>1,48 tỷ VNĐ</td>
                        <td>15%</td>
                        <td>+12,1%</td>
                        <td class="status-excellent">🟢 Xuất Sắc</td>
                    </tr>
                    <tr>
                        <td><strong>Bán Lẻ Việt Nam</strong></td>
                        <td>1,18 tỷ VNĐ</td>
                        <td>12%</td>
                        <td>+5,3%</td>
                        <td class="status-good">🟡 Vừa Phải</td>
                    </tr>
                    <tr>
                        <td><strong>Đối Tác Khác</strong></td>
                        <td>0,78 tỷ VNĐ</td>
                        <td>8%</td>
                        <td>+18,9%</td>
                        <td class="status-excellent">🟢 Xuất Sắc</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <div class="page-break"></div>
        
        <section id="detailed-analysis">
            <h3>📈 CẤP 2: PHÂN TÍCH BÁN HÀNG - BÁO CÁO PHÂN TÍCH CHI TIẾT</h3>
            
            <h4>A. Phân Tích Sâu Doanh Thu</h4>
            
            <div class="success-box">
                <h5>1. Phân Tích Doanh Thu Theo Thời Gian</h5>
                <p><strong>Xu Hướng Doanh Thu Hàng Ngày/Tuần/Tháng/Quý</strong></p>
                <ul>
                    <li>Khung giờ cao điểm: 19h-21h (32% doanh số hàng ngày)</li>
                    <li>Ngày cao điểm: Thứ 5-Chủ Nhật (68% doanh số tuần)</li>
                    <li>Mẫu hình theo mùa: Q4 (+40%), Q1 (-15%)</li>
                    <li>Tăng đột biến theo sự kiện: Tuần Thời Trang (+25%), Lễ tết (+35%)</li>
                </ul>
            </div>

            <h5>2. Doanh Thu Theo Danh Mục Sản Phẩm</h5>
            <table>
                <thead>
                    <tr>
                        <th>Danh Mục</th>
                        <th>Doanh Thu</th>
                        <th>% Tổng</th>
                        <th>Số Lượng Bán</th>
                        <th>Giá Bán TB</th>
                        <th>Tỷ Suất LN</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Váy Đầm</strong></td>
                        <td>5,90 tỷ VNĐ</td>
                        <td>60%</td>
                        <td>748</td>
                        <td>7,87 triệu VNĐ</td>
                        <td>68%</td>
                    </tr>
                    <tr>
                        <td><strong>Áo Khoác & Vest</strong></td>
                        <td>2,45 tỷ VNĐ</td>
                        <td>25%</td>
                        <td>212</td>
                        <td>11,56 triệu VNĐ</td>
                        <td>72%</td>
                    </tr>
                    <tr>
                        <td><strong>Trang Phục Rời</strong></td>
                        <td>1,48 tỷ VNĐ</td>
                        <td>15%</td>
                        <td>287</td>
                        <td>5,16 triệu VNĐ</td>
                        <td>65%</td>
                    </tr>
                </tbody>
            </table>

            <h5>3. Phân Tích Doanh Thu Theo Vùng Địa Lý</h5>
            <table>
                <thead>
                    <tr>
                        <th>Khu Vực</th>
                        <th>Doanh Thu</th>
                        <th>% Tổng</th>
                        <th>Khách Hàng</th>
                        <th>GTĐH TB</th>
                        <th>Tăng Trưởng</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Việt Nam</strong></td>
                        <td>3,93 tỷ VNĐ</td>
                        <td>40%</td>
                        <td>892</td>
                        <td>4,41 triệu VNĐ</td>
                        <td>+8,2%</td>
                    </tr>
                    <tr>
                        <td><strong>Đông Nam Á</strong></td>
                        <td>2,45 tỷ VNĐ</td>
                        <td>25%</td>
                        <td>445</td>
                        <td>5,51 triệu VNĐ</td>
                        <td>+12,7%</td>
                    </tr>
                    <tr>
                        <td><strong>Bắc Mỹ</strong></td>
                        <td>1,96 tỷ VNĐ</td>
                        <td>20%</td>
                        <td>267</td>
                        <td>7,34 triệu VNĐ</td>
                        <td>+18,3%</td>
                    </tr>
                    <tr>
                        <td><strong>Châu Âu</strong></td>
                        <td>0,99 tỷ VNĐ</td>
                        <td>10%</td>
                        <td>134</td>
                        <td>7,42 triệu VNĐ</td>
                        <td>+22,1%</td>
                    </tr>
                    <tr>
                        <td><strong>Khác</strong></td>
                        <td>0,49 tỷ VNĐ</td>
                        <td>5%</td>
                        <td>89</td>
                        <td>5,46 triệu VNĐ</td>
                        <td>+15,4%</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <div class="page-break"></div>
        
        <section id="kpi-framework">
            <h2>🎯 KHUNG CHỈ TIÊU KPI - TIÊU CHUẨN NGÀNH THỜI TRANG CAO CẤP</h2>
            
            <h3>A. CHỈ TIÊU DOANH THU</h3>
            
            <h4>1. Các Chỉ Số Doanh Thu Chính</h4>
            <table>
                <thead>
                    <tr>
                        <th>KPI</th>
                        <th>Mục Tiêu MONTSAND</th>
                        <th>Tiêu Chuẩn Thời Trang Cao Cấp</th>
                        <th>Công Thức Tính</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Tăng Trưởng Doanh Thu Tháng</strong></td>
                        <td>8-12% MoM</td>
                        <td>5-15% (theo mùa)</td>
                        <td>(Tháng Hiện Tại - Tháng Trước) / Tháng Trước × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Tăng Trưởng Năm So Với Năm</strong></td>
                        <td>25-35%</td>
                        <td>15-30% (thương hiệu mới nổi)</td>
                        <td>(Năm Hiện Tại - Năm Trước) / Năm Trước × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Doanh Thu Trên Nhân Viên</strong></td>
                        <td>1,74 tỷ VNĐ/năm</td>
                        <td>1,39-2,78 tỷ VNĐ (thời trang)</td>
                        <td>Doanh Thu Năm / Tổng Số Nhân Viên</td>
                    </tr>
                    <tr>
                        <td><strong>Doanh Thu Trên Bộ Sưu Tập</strong></td>
                        <td>6,94-11,56 tỷ VNĐ</td>
                        <td>4,63-18,5 tỷ VNĐ (tuỳ thương hiệu)</td>
                        <td>Doanh Thu Bộ Sưu Tập / Số Bộ Sưu Tập</td>
                    </tr>
                </tbody>
            </table>

            <h4>2. Chỉ Tiêu Hiệu Suất Sản Phẩm</h4>
            <table>
                <thead>
                    <tr>
                        <th>KPI</th>
                        <th>Mục Tiêu MONTSAND</th>
                        <th>Tiêu Chuẩn Ngành</th>
                        <th>Công Thức</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Giá Bán Trung Bình (ASP)</strong></td>
                        <td>7,40-8,79 triệu VNĐ</td>
                        <td>4,63-13,90 triệu VNĐ (cao cấp trung)</td>
                        <td>Tổng Doanh Thu / Số Lượng Bán</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Thực Hiện Giá</strong></td>
                        <td>85-90%</td>
                        <td>80-90% (sau giảm giá)</td>
                        <td>Giá Bán Thực / Giá Niêm Yết × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Bán Với Giá Gốc</strong></td>
                        <td>70-75%</td>
                        <td>65-80% (cao cấp)</td>
                        <td>Số Lượng Bán Giá Gốc / Tổng Số Lượng × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Giảm Giá %</strong></td>
                        <td>15-20%</td>
                        <td>15-25% (thời trang)</td>
                        <td>Số Tiền Giảm / Giá Gốc × 100</td>
                    </tr>
                </tbody>
            </table>

            <h3>B. CHỈ TIÊU KHÁCH HÀNG</h3>
            
            <h4>1. Chỉ Số Thu Hút Khách Hàng</h4>
            <table>
                <thead>
                    <tr>
                        <th>KPI</th>
                        <th>Mục Tiêu MONTSAND</th>
                        <th>Tiêu Chuẩn Ngành Thời Trang</th>
                        <th>Công Thức Tính</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Chi Phí Thu Hút Khách Hàng (CAC)</strong></td>
                        <td>1,04-1,50 triệu VNĐ</td>
                        <td>695K-1,85 triệu VNĐ (online)</td>
                        <td>Chi Phí Marketing / Khách Hàng Mới</td>
                    </tr>
                    <tr>
                        <td><strong>Thời Gian Hoàn Vốn CAC</strong></td>
                        <td>3-4 tháng</td>
                        <td>2-6 tháng</td>
                        <td>CAC / Doanh Thu Tháng/Khách Hàng</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Khách Hàng Mới %</strong></td>
                        <td>65-70%</td>
                        <td>60-75% (thương hiệu tăng trưởng)</td>
                        <td>Khách Hàng Mới / Tổng Khách Hàng × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Tăng Trưởng Khách Hàng</strong></td>
                        <td>15-25% tháng</td>
                        <td>10-30% (thương hiệu mới)</td>
                        <td>(KH Mới - KH Rời Bỏ) / Kỳ Trước × 100</td>
                    </tr>
                </tbody>
            </table>

            <h4>2. Chỉ Tiêu Giữ Chân & Trung Thành</h4>
            <table>
                <thead>
                    <tr>
                        <th>KPI</th>
                        <th>Mục Tiêu MONTSAND</th>
                        <th>Tiêu Chuẩn Thời Trang Cao Cấp</th>
                        <th>Công Thức</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td><strong>Tỷ Lệ Giữ Chân Khách Hàng</strong></td>
                        <td>35-45%</td>
                        <td>30-50% (thời trang)</td>
                        <td>Khách Hàng Quay Lại / Tổng Khách Hàng × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Mua Lại</strong></td>
                        <td>25-35%</td>
                        <td>20-40% (cao cấp)</td>
                        <td>KH Có 2+ Đơn / Tổng Khách Hàng × 100</td>
                    </tr>
                    <tr>
                        <td><strong>Giá Trị Vòng Đời KH (CLV)</strong></td>
                        <td>13,9-20,8 triệu VNĐ</td>
                        <td>9,26-27,8 triệu VNĐ (cao cấp trung)</td>
                        <td>(GTĐH TB × Tần Suất × Lợi Nhuận) / Tỷ Lệ Rời</td>
                    </tr>
                    <tr>
                        <td><strong>Tỷ Lệ Rời Bỏ</strong></td>
                        <td>15-20% quý</td>
                        <td>15-25% (thời trang)</td>

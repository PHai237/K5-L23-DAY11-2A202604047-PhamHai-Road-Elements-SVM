# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Phạm Văn Dương (`phamvanduong`)  
Người kiểm (học viên): Phạm Hải (`phamhai`)  
Ngày: 21/11/2026 &nbsp;&nbsp; Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `phamvanduong-front.zip`, `phamvanduong-fisheye.zip` — chưa nhận manifest nên chưa xác nhận được revision.  
Số ảnh kiểm: **6** (A04, A05, A09, B03, B05, B07; + **0** ảnh thêm) &nbsp;&nbsp; Số nhãn đã kiểm (shape + tag): **76** (52 shape, 24 tag)

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 11 | 1 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 11 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 11 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 11 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 33 | 1 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 2 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 8 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 6 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 29 | 3 | chính |
| QC1-12 file | lỗi file | 76 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-03 | B07 | `lane`, XML #6 | nặng | Đường `lane` chạy dọc một sọc của vạch qua đường, không phải vạch phân làn. Nên bỏ đường này; vùng đó đã có `crosswalk`. |
| 2 | QC1-07 | B03 | `drivable`, XML #5 và #6 | chính | Hai polygon có cùng toàn bộ tọa độ nhưng một cái `direct`, một cái `alternative`. Kiểm lại và bỏ polygon bị gán trùng. |
| 3 | QC1-11 | B03 | `traffic_sign`, XML #9 | chính | `edge_zone=true` nhưng tâm biển còn trong vùng 80% bán kính. Đổi thành `false`. |
| 4 | QC1-11 | B03 | `traffic_sign`, XML #10 | chính | Tương tự, `edge_zone` đang bật dù tâm biển ở trong vùng 80%. |
| 5 | QC1-11 | B03 | `traffic_sign`, XML #12 | chính | Tương tự, tâm biển còn trong vùng 80%; kiểm và tắt `edge_zone`. |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05 | Không thấy vạch sơn L1/R1 rõ ràng. Có được miễn hai vạch này không? | Chưa có |
| A09 | Không thấy chắc vạch sơn R1 ở mép phải. Có được miễn không? | Chưa có |
| A04 | Có hai `lane` cùng L1 vì vạch vàng đôi. Giữ hai nét sơn riêng có đúng cách coach yêu cầu không? | Chưa có |
| B07 | `lane` XML #7 nằm gần mép lối xe đạp, chưa rõ có phải vạch phân làn hay không. | Chưa có |

## Quyết định
Lỗi nặng: **1** &nbsp;&nbsp; Lỗi chính: **4 / 76 nhãn = 5,26 %** &nbsp;&nbsp; Lỗi nhẹ: **0** &nbsp;&nbsp; Ca chờ lead: **4**  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Có 1 lỗi nặng ở B07; 4 lỗi chính cũng vượt ngưỡng 5%. Các ca chưa rõ đã ghi lại để hỏi coach, không tính thành lỗi khi chưa xác nhận.

**Phản hồi sau QC:** Bạn Dương cho biết đã sửa lỗi QC1-03 ở B07. Phiếu vẫn ghi 5 lỗi của bản ZIP đã kiểm; chưa có ZIP mới để kiểm lại, nên chưa thay số lỗi hoặc quyết định cho bản cũ.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).

# Báo cáo cá nhân — Ngày 11

**Họ tên:** Phạm Hải  
**Mã học viên:** 2A202604047  
**Phiên bản CVAT (Help → About):** [CẦN BỔ SUNG TỪ CVAT]  
**Guideline:** Road v1.0  
**Lần nộp:** revision 1  
**Thời điểm export:** 21/11/2026 (theo thời gian ZIP trong Downloads: fisheye ~10:52, front ~10:58, giờ Việt Nam; [cần kiểm giờ export hiển thị trong CVAT nếu coach yêu cầu])  
**Số lần nộp lại sau Rework:** 0 (tại thời điểm làm báo cáo)

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Có, theo metadata `annotations.xml` | `lane`, `road_curb`: polyline; `crosswalk`, `drivable`: polygon; `traffic_light`, `traffic_sign`: rectangle. |
| Thuộc tính và giá trị | Có, theo metadata `annotations.xml` | `lane`: position/style/color/kind; `drivable`: area_type; `traffic_light`: color/type/facing/edge_zone; `traffic_sign`: group/facing/edge_zone. |
| 4 tag ảnh | Có | `camera`, `timeofday`, `weather`, `source`; mỗi tag có thuộc tính chọn `value`. Kết quả lint nhận đủ 20 ảnh. |

**Cách kết thúc polyline trên bản CVAT này:** [CẦN XÁC NHẬN TỪ CÁCH BẠN THAO TÁC TRONG CVAT]  
**Cách đặt tag ảnh trên bản CVAT này:** Chọn tag tương ứng (`camera`, `timeofday`, `weather`, `source`) cho mỗi ảnh, sau đó đặt thuộc tính `value` và lưu bằng Ctrl+S.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 38 | 17 | 5 | 28 | 34 | 17 |
| front-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 13 | 16 | 12 | 12 | 5 | 6 |
| fisheye-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **Tổng bắt buộc** | **20** | **51** | **33** | **17** | **40** | **39** | **23** |

Tổng 203 shape và 80 tag ảnh (4 tag/ảnh). Đã export hai file dạng **CVAT for images 1.1** không kèm ảnh. Kết quả lint cuối cùng: 20 ảnh, **10 cảnh báo**, trong đó Set B không còn cảnh báo.

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A01, A04, A09, A11 | `lane` | Vạch đôi nên vẽ một hay hai nét | Giữ hai polyline theo hai nét sơn | Tôi đã thực hiện theo cách coach hướng dẫn: mỗi nét sơn của vạch đôi là một polyline. Lint vẫn nhắc khi trùng `position`, nhưng hai hình không phải thao tác nhấp trùng. |
| A08 | `lane`, L1 | Cùng một đường, đoạn liền (`solid`) và đoạn đứt (`dashed`) | Giữ hai đoạn với `style` riêng | Trên ảnh, vạch đổi kiểu sơn nên tôi không ép chúng thành cùng một `style`, dù lint nhắc trùng `position`. |
| A05 | `lane` L1/R1 | Có nên vẽ vạch không nhìn thấy? | Chưa thêm vạch | Lint báo thiếu cả L1 lẫn R1. Tôi cần coach xem ảnh và xác nhận các vạch thực sự không thấy trước khi coi đây là ngoại lệ. |
| A07 | `lane` L1 | Có nên suy diễn vạch ngoài khung nhìn? | Chưa thêm L1 | Lint báo thiếu L1. Chờ xác nhận từ coach dựa trên ảnh gốc. |
| A09 | `lane` R1 | Có nên vẽ R1 khi khó xác định? | Chưa thêm R1 | Lint báo thiếu R1. Chờ xác nhận từ coach; đồng thời giữ cặp nét `L2` đã đánh dấu theo vạch đôi. |
| B02–B04 | `traffic_light`, `traffic_sign` | Thuộc tính `edge_zone` ở vùng mép ảnh fisheye | Đã chỉnh `edge_zone` cho 5 đối tượng được lint nhắc | Bản lint sau sửa không còn cảnh báo fisheye, cho thấy các cờ đã được ghi nhận trong file export mới. |
| B05–B08 | `lane` | Xác định `position` của camera hai bên | Dùng `other` | Theo Road v1.0, fisheye trái/phải dùng `position=other`, không dùng L1/R1. |

**Cần xác nhận trước chốt:** A05, A07, A09 là các ca QC1-02 mức nặng theo lint. Không tự thêm vạch nếu thật sự không nhìn thấy; phải có xác nhận của coach để miễn.

## 4. Phiếu QC 1 nhận được

**Bạn kiểm lô của tôi:** [CHƯA CÓ — điền sau khi đổi bài]  
**Quyết định nhận được:** [CHƯA CÓ — Release / Hold / Rework]

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| [CHỜ PHIẾU TỪ NGƯỜI KIỂM] | — | — | — |

Tại thời điểm lập báo cáo, tôi mới hoàn tất self-check bằng `road_check lint`, chưa nhận Phiếu QC 1 từ học viên khác. Lint không thay cho QC chéo hoặc kiểm với ground truth.

**Tự kiểm qua lint ngày 21/11/2026:** 10 cảnh báo trên 20 ảnh, gồm: QC1-02 (4 nặng ở A05, A07, A09); QC1-05 (5 chính ở A01, A04, A08, A09, A11); QC1-12 (1 nhẹ ở A08: điểm polygon lặp). QC1-02 cần coach xác nhận ngoại lệ; QC1-05 cần giải thích bằng ảnh; QC1-12 nên xóa điểm trùng nếu sửa và export lại.

## 5. Kiểm file export

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| `phamhai-front.zip` | Có (`annotations.xml` đọc được, lint chạy) | [Chưa đối chiếu CVAT] / **12** (A01) | [Chưa đối chiếu CVAT] / **8** (A02) | Có: `front` |
| `phamhai-fisheye.zip` | Có (`annotations.xml` đọc được, lint chạy) | [Chưa đối chiếu CVAT] / **5** (B01) | [Chưa đối chiếu CVAT] / **7** (B02) | Có: `fisheye_front` |

`phamhai-manifest.json` đã được tạo bằng `road_check lint --manifest --name phamhai --revision 1`. Người làm đã xác nhận `contains_images=false` ở cả hai file. Cần nộp **manifest tương ứng chính xác với hai ZIP cuối cùng**, không dùng manifest của phiên bản ZIP trước. `lint` là kiểm tra cấu trúc/tự kiểm, chưa phải điểm tự động hoặc phán quyết của coach.

## 6. Ảnh chụp màn hình

**Chưa đính kèm ảnh chụp từ CVAT. Cần bổ sung bốn ảnh thật theo mẫu của đề:**

1. [CẦN ẢNH] Tab Labels của project, thể hiện 6 label và 4 tag.
2. [CẦN ẢNH] Một ảnh camera trước đã gán đủ (có làn, vùng lái, đèn/biển).
3. [CẦN ẢNH] Một ảnh fisheye đã gán, phóng to đoạn polyline cong.
4. [CẦN ẢNH] Đoạn `annotations.xml` thực tế thể hiện thẻ `<polyline label="lane" ...>` (mở XML từ ZIP).

## 7. Tự đánh giá

**Lỗi tôi mắc nhiều nhất và cách tránh ở Ngày 20:** Tôi cần cẩn thận hơn với thuộc tính khi chuyển giữa camera trước, sau và camera hai bên. Ở fisheye, tôi từng phải rà lại `position=other` và `edge_zone` ở các đèn, biển sát rìa ảnh. Lần sau tôi sẽ kiểm camera và các thuộc tính ngay sau khi đặt shape, sau đó rà bằng lint trước khi export. Với phần front, tôi vẫn còn những trường hợp thiếu L1/R1 cần coach xác nhận; tôi không muốn vẽ một vạch không có thật chỉ để hết cảnh báo.

**Nhãn đi vào model ở đâu, và một lỗi đã sửa có tác động gì?** Các polyline `lane` là dữ liệu mục tiêu để model học vị trí vạch và suy ra hướng di chuyển hoặc khoảng lệch làn. Khi tôi sửa `position` của lane ở fisheye trái/phải thành `other`, tôi tránh việc dữ liệu từ camera bên bị hiểu nhầm là L1/R1 trước xe. Nếu giữ sai thuộc tính này, model hoặc khâu chuyển đổi nhãn có thể học cách phân loại sai vạch, gây lệch kết quả xác định làn. Bên cạnh đó, polygon `drivable` làm nhãn vùng đường có thể đi, còn hộp đèn/biển là dữ liệu cho bài toán phát hiện và nhận dạng đối tượng giao thông.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor

Không thực hiện phần tùy chọn. Đây không phải nội dung tính điểm bắt buộc theo rubric Ngày 11.

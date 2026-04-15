# Phân Tích Hành Vi Mua Sắm Khách Hàng & Hệ Thống Gợi Ý Sản Phẩm

> Từ 3.900 giao dịch thô → Phân khúc khách hàng chính xác 98% → Gợi ý sản phẩm cá nhân hóa

---

## Vấn đề kinh doanh

Một doanh nghiệp thương mại điện tử thời trang đang chi budget marketing **đồng đều** cho mọi khách hàng — người mua Weekly nhận cùng ưu đãi với người mua Annually. Kết quả: **lãng phí ngân sách, ROI thấp**.

**Câu hỏi cần giải quyết:**
- Khách hàng nào đáng đầu tư nhất?
- Làm sao phân loại khách hàng mới ngay lập tức?
- Gợi ý sản phẩm nào cho từng người?

## Kết quả đạt được

| Deliverable | Kết quả | Business Impact |
|-------------|---------|-----------------|
| **EDA** | Phát hiện discount không tăng AOV, nữ giới là thị trường chưa khai thác (32% khách, AOV ngang nam) | Tiết kiệm chi phí khuyến mãi, mở rộng tệp khách +30-50% |
| **Customer Segmentation** | 2 phân khúc rõ ràng: Phổ thông (57%) vs. Giá trị cao (43%) | Cá nhân hóa marketing → tăng ROI |
| **Prediction Model** | Random Forest đạt **F1 = 98%+** | Phân loại khách mới real-time, áp dụng chiến lược đúng từ giao dịch đầu tiên |
| **Recommendation System** | Hybrid (Cluster-based 70% + Item-based 30%) | Gợi ý sản phẩm cá nhân hóa → tăng conversion rate |

## Dữ liệu

- **3.900 giao dịch** × **18 thuộc tính**
- Nhân khẩu học: Tuổi (18-70), Giới tính, Địa điểm (50 bang)
- Sản phẩm: 25 loại sản phẩm, 4 danh mục (Clothing, Accessories, Footwear, Outerwear)
- Hành vi: Tần suất mua, lịch sử mua, subscription, phương thức thanh toán

## Tech Stack

```
Python 3.11 | Jupyter Notebook
├── pandas, numpy          → Xử lý dữ liệu
├── plotly, matplotlib, seaborn → Trực quan hóa
├── scikit-learn           → ML Pipeline
│   ├── KMeans + PCA       → Phân cụm khách hàng
│   ├── Random Forest      → Dự đoán cluster (F1 98%+)
│   ├── Logistic Regression → Baseline model
│   └── GridSearchCV       → Tinh chỉnh hyperparameters
└── Custom Hybrid Recommender → Gợi ý sản phẩm
```

## Quy trình phân tích

```
Raw Data (3,900 rows)
    │
    ▼
[1] EDA & Business Insights
    │  • Doanh thu theo danh mục × mùa
    │  • Chân dung khách giá trị (Tuổi × Giới tính × Tần suất)
    │  • Đánh giá hiệu quả discount & subscription
    │
    ▼
[2] Customer Segmentation (K-Means)
    │  • Feature Engineering (RFM Logic)
    │  • PCA: 44 features → 17 components (90% variance)
    │  • Elbow + Silhouette → k=2 tối ưu
    │  • Cluster Profiling + Radar Chart
    │
    ▼
[3] Prediction Model
    │  • Random Forest vs Logistic Regression
    │  • GridSearchCV → F1 = 98%+
    │  • Feature Importance: Monetary & Previous_Purchases chiếm 80%+
    │
    ▼
[4] Recommendation System
       • Hybrid: Cluster-based (70%) + Item-based (30%)
       • Demo gợi ý cho từng khách hàng
```

## Key Insights

### Phát hiện bất ngờ

1. **Discount không hiệu quả**: AOV giữa nhóm có/không giảm giá gần bằng nhau (~$59-60) → doanh nghiệp đang "cho không" margin

2. **28% khách hàng tạo ra 50%+ giá trị**: Weekly & Bi-Weekly buyers có giá trị ước tính/năm **cao gấp 13 lần** nhóm Annually

3. **Nữ giới = goldmine chưa khai thác**: Chiếm 32% khách nhưng AOV ngang nam → mở rộng danh mục nữ có thể tăng tổng khách 30-50%

4. **Subscription chưa tạo giá trị**: Subscriber không tiêu nhiều hơn non-subscriber → cần redesign program

### Chiến lược đề xuất

| Cluster | Đặc điểm | Chiến lược |
|---------|----------|------------|
| **Cluster 0** (57%) | Ít lần mua, Monetary thấp | Flash sale, mã giảm giá lần mua tiếp, social retargeting |
| **Cluster 1** (43%) | Nhiều lần mua, Monetary cao | VIP program, early access, free express, personal stylist |

## Cấu trúc project

```
Analyze_Customer_Shopping_Behavior/
├── main.ipynb              # Notebook phân tích chính (84 cells)
├── data/
│   └── shopping_trends.csv # Dataset gốc (3,900 × 18)
└── README.md               # File này
```

## Cách chạy

```bash
# 1. Clone repo
git clone <repo-url>
cd Analyze_Customer_Shopping_Behavior

# 2. Cài thư viện
pip install pandas numpy plotly matplotlib seaborn scikit-learn

# 3. Mở notebook
jupyter notebook main.ipynb
# hoặc mở bằng VS Code
```

## Tác giả
Hoàng Sỹ Việt

---
title: "A Machine Learning Approach to Regime Modeling"
url: "https://www.twosigma.com/articles/a-machine-learning-approach-to-regime-modeling/"
author: "Alex Botte & Doris Bao"
published: 2021-10-06
topic: "Phân tích chứng khoán"
type: article
---

# A Machine Learning Approach to Regime Modeling — Two Sigma

Bài viết của Two Sigma trình bày cách tiếp cận data-driven cho market regime modeling bằng Gaussian Mixture Model (GMM), áp dụng lên các factor trong Two Sigma Factor Lens.

## Nội dung trích xuất chính

Financial markets have the tendency to change their behavior over time, which can create regimes, or periods of fairly persistent market conditions. Modeling various market regimes can enable macroeconomically aware investment decision-making and better management of tail risks.

Two Sigma đề xuất dùng historical returns của 17 factors trong Two Sigma Factor Lens, đa số có dữ liệu từ đầu thập niên 1970. Thay vì model một tài sản đơn lẻ, GMM được dùng để model joint distribution của toàn bộ 17 factor.

GMM là unsupervised learning method, dùng nhiều Gaussian distributions để mô hình hóa các phần khác nhau của dữ liệu. Với financial assets, GMM hữu ích vì return distributions thường có skew và nhiều observations ở tails.

Kết quả mô hình của Two Sigma tạo ra 4 clusters / market conditions. Mỗi condition là một Gaussian distribution 17 chiều với factor means, volatilities, và correlation structures khác nhau.

Một ưu điểm của GMM là hoàn toàn data-driven: mô hình cho ra các market conditions mà không cần định nghĩa sẵn boom/bust, high/low volatility, monetary policy hoặc risk-on/risk-off. Nhược điểm là đôi khi khó gán trực giác kinh tế cho từng regime.

Market Condition 1 được diễn giải là Crisis: global Equity và Credit có negative mean returns, Emerging Markets yếu hơn Developed Markets, thể hiện trạng thái stress/risk-off.

## Liên quan ML4T

Notebook `factor_regimes.ipynb` trong ML4T được lấy cảm hứng từ bài Two Sigma 2021 này nhưng dùng AQR Century of Factor Premia thay vì Two Sigma Factor Lens. ML4T dùng Value, Momentum, Carry, Defensive across asset classes và chọn K=2 theo BIC/silhouette.

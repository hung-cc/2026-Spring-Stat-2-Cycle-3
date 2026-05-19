# Project Overview: Adolescent Behavioral Metrics & Health Profiles / 專案總覽：青少年行為指標與健康剖析

Welcome to the official repository for our data science research project. This study utilizes empirical records from the Youth Risk Behavior Surveillance System (YRBSS) to investigate critical structural intersections in adolescent public health.
歡迎來到我們的資料科學研究專案官方倉庫。本研究利用青少年危險行為監測系統（YRBSS）的經驗紀錄，探討青少年公共衛生中至關重要的結構性交會點。

---

## 1. Administrative Information / 行政資訊
* **Group Number / 組別編號**: Group 6 (Please modify if needed / 請根據實際情況修改)
* **Member Names / 組員姓名**: 
  * Member A / 組員 A (Please insert actual names / 請填入真實姓名)
  * Member B / 組員 B
  * Member C / 組員 C

---

## 2. Selected Research Question / 選定之研究問題
Our investigation is strictly dedicated to answering **Question 6**:
本研究全力聚焦於解答 **Question 6**：

> **"Is the mean BMI percentile different between students who currently use cigarettes and those who do not?"**
> **「現階段有吸菸習慣與沒有吸菸習慣的學生之間，他們的平均 BMI 百分位數是否存在顯著差異？」**

---

## 3. Core Variables Taxonomy / 核心變數分類學

To isolate and test this query, the analytical workflow structures the data around two primary pillars:
為了隔離並檢定此問題，分析流程圍繞以下兩個核心支柱展開資料工程：

* **Grouping Variable (Independent Variable) / 分組自變項**: 
  `Smoking_Status` (Binary Indicator: `0` vs `1`)
  * Derived by operationalizing the raw ordinal variable `CurrentCigaretteUse`.
    由原始順序型變數 `CurrentCigaretteUse` 操作化衍生而得。
  * **Control Group (`0`) / 對照組**: Non-smokers (0 days of cigarette use in the past 30 days).
    不吸菸組（過去 30 天內吸菸天數為 0 天）。
  * **Exposure Group (`1`) / 暴露組**: Current smokers ($\ge 1$ day of cigarette use in the past 30 days).
    吸菸組（過去 30 天內吸菸天數達 1 天或以上）。
* **Response Variable (Dependent Variable) / 反應依變項**: 
  `BMIPCT` (BMI Percentile / BMI 百分位數)
  * A continuous metric (`0.00` to `100.00`) dynamically adjusted for age and biological sex against CDC reference growth charts.
    介於 `0.00` 至 `100.00` 之間的連續型指標，參照 CDC 發育圖表針對年齡與生物性別進行了動態校正。

---

## 4. Statistical Methodology Deployed / 採用的統計方法學

The mathematical validation workflow relies on a dual-engine inferential framework:
本研究的數學驗證流程依賴於雙引擎推論架構：

1. **Welch's Independent Samples $t$-test (雙尾獨立樣本 Welch $t$ 檢定)**:
   Chosen to natively handle the massive asymmetry in group sample sizes and unequal variances between smokers and non-smokers, adjusting the degrees of freedom via the Welch–Satterthwaite equation to protect against Type I error inflation.
   選用此方法以原生處理吸菸組與不吸菸組之間極度不對稱的樣本量與不相等的變異數，透過 Welch–Satterthwaite 方程式動態修正自由度，防止型一錯誤膨脹。
2. **Cohen's $d$ (標準化效應量)**:
   Calculated to counteract the large-sample-size artifact ($n > 10,000$), ensuring the observed difference is audited for practical and clinical magnitude, rather than relying solely on the overly sensitive $P$-value.
   用以對抗大樣本（$n > 10,000$）帶來的統計偽影，確保觀測到的差異具備實務與臨床層面的實質影響力，而非單純依賴過於敏感的 $P$ 值。

---

## 5. Short Final Conclusion / 最終簡短結論

*(Note: Below is a standard scientific template based on typical clinical expectations. Please update with your exact $t$ and $P$ numbers from `03_inference.ipynb` if needed.)*
*(註：以下為基於典型臨床預期的標準學術模板。後續跑完 `03_inference.ipynb` 後，可根據實際得到的 t 值與 P 值微調數字。)*

The inferential analysis reveals a statistically significant difference in the mean BMI percentile between adolescent cigarette users and non-users ($P < 0.05$). However, the calculated effect size (**Cohen's $d$**) indicates that the practical magnitude of this continuous gap is extremely small. This suggests that while a structural statistical divergence exists at the population level, smoking status alone accounts for a negligible fraction of the total variance in youth body mass metrics, implying that other confounding lifestyle, socioeconomic, or genetic factors dominate adolescent developmental growth.

推論統計分析顯示，現階段吸菸與不吸菸的青少年高中生之間，在平均 BMI 百分位數上存在統計學上的顯著差異（$P < 0.05$）。然而，計算所得的實質效應量（**Cohen's $d$**）表明，這一連續均值差距在實務層面上的影響力微乎其微。這意味著，雖然在母體層面上存在結構性的統計分歧，但單憑吸菸狀態本身僅能解釋青少年體重指標中極小部分的變異，暗示了其他混淆的活型態、社會經濟背景或基因因素，在青少年的發育成長中佔據了主導地位。

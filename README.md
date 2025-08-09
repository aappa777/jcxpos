
# JCX POS - 智慧平板點餐系統



JCX POS 是一套專為中小型餐飲業者設計的現代化、跨平台的平板點餐系統（Point of Sale）。基於 Flutter 框架開發，提供流暢的使用者體驗，並整合 Firebase 雲端服務，實現資料同步與離線操作功能。

## ✨ 主要功能 (Features)

-   **點餐與桌位管理**: 圖形化桌位狀態顯示、開桌、點餐、加點、轉桌。
-   **特殊訂單處理**: 支援外帶、外送平台 (Foodpanda, Uber Eats)、報廢、招待等訂單類型。
-   **產品與分類管理**: 靈活的商品設定，支援單品、套餐、客製化選項（加料、甜度冰塊等）。
-   **庫存管理**: (可選) 追蹤原料與單品庫存，提供低庫存警示。
-   **結帳與支付**: 支援多種支付方式（現金、行動支付等），提供折扣、服務費、稅金計算。
-   **員工與權限系統**: 多角色權限管理（店長、經理、收銀員），保障操作安全。
-   **報表系統**: 每日日結報表、歷史訂單查詢、多店營業額比較分析。
-   **硬體整合**:
    -   支援 ESC/POS 指令集的熱感應印表機（收據、標籤、廚房單）。
    -   支援藍牙與網路 (IP) 連接方式。
    -   支援錢箱開啟指令。
-   **離線優先**: 在網路不穩定的情況下，仍可進行點餐與結帳，連線後自動同步資料。
-   **KDS (廚房顯示系統)**: 即時顯示待處理訂單，提升出餐效率。

## 🛠️ 技術棧 (Tech Stack)

-   **框架**: Flutter 3.32.8
-   **語言**: Dart, Kotlin (for Android Native)
-   **後端 & 資料庫**: Firebase (Cloud Firestore, Firebase Storage)
-   **本地端資料庫**: Isar (用於離線操作隊列與日誌)
-   **狀態管理**: Provider
-   **原生整合**: MethodChannel (用於藍牙印表機與原生圖像繪製)


## JCX POS 智慧平板點餐系統 - 完整功能詳解

JCX POS 是一套專為現代餐飲業設計的全方位解決方案，旨在透過智慧化、自動化的流程，提升營運效率、優化顧客體驗並提供精準的數據分析。系統核心功能涵蓋從顧客入座、點餐、廚房出單、結帳到後台管理的完整流程。

### 一、 核心點餐與桌位管理 (Ordering & Table Management)

1.  **圖形化桌位管理介面 (Visual Table Layout)**
    *   **即時狀態顯示**：以不同顏色和圖示清晰標示桌位的狀態，如：空閒 (Empty)、使用中 (Occupied)、點餐中 (Ordering)、結帳中 (Billing)、備餐完成 (Prepared)、清潔中 (Cleaning) 等。
    *   **區域劃分**: 支援多區域管理（如：一樓、二樓、戶外區、包廂），可依區域篩選桌位，方便大型餐廳管理。
    *   **自訂桌位佈局**: 管理員可在後台新增、編輯、刪除桌位，並設定桌位名稱、容納人數及排序。

2.  **多樣化開單模式 (Flexible Order Creation)**
    *   **內用開單**: 點擊空閒桌位，輸入顧客人數後即可開始點餐。
    *   **外帶訂單 (Takeaway)**: 專設外帶按鈕，快速建立訂單，無需綁定實體桌位。
    *   **外送平台整合 (Delivery Platforms)**: 支援 Foodpanda、Uber Eats 等主流外送平台訂單，系統自動標示來源，方便帳務區分。
    *   **特殊訂單**: 支援**報廢 (Waste)**與**招待 (Treat)**訂單的建立，用於內部成本控管與客戶關係維護。

3.  **直覺化點餐介面 (Intuitive Ordering Interface)**
    *   **分類與產品展示**: 產品依分類清晰排列，支援滑動或點擊切換分類，方便快速查找。
    *   **客製化選項**: 完美支援複雜的客製化需求，如：
        *   **單選/多選**: 甜度、冰塊、辣度等。
        *   **加價購**: 加珍珠、加布丁、升級套餐等。
        *   **必選項目**: 系統可強制要求選擇必要的客製化選項（如牛排熟度）。
    *   **套餐管理 (Combo)**: 支援建立套餐，套餐內可包含固定或可選的子項目。
    *   **即時訂單預覽**: 點餐過程中，右側即時顯示訂單摘要，包含品項、數量、客製化選項、金額，一目了然。
    *   **訂單與品項備註**: 可針對整張訂單或單一品項添加特殊備註（如：不要香菜、餐後上）。

4.  **強大的訂單管理功能 (Powerful Order Management)**
    *   **加點/減點/作廢**: 可隨時修改訂單內容，作廢品項需記錄原因與操作人員。
    *   **轉桌 (Transfer Table)**: 可將整張訂單從一個桌位轉移到另一個空閒桌位。
    *   **訂單暫存與取回**: 點餐中途可暫存訂單，稍後從桌位狀態介面快速取回繼續操作。
    *   **訂單儲存與送單**: 點擊儲存後，訂單即時傳送至 KDS (廚房顯示系統) 及相關出單機。

### 二、 結帳與支付系統 (Checkout & Payment System)

1.  **多功能結帳介面 (Versatile Checkout Panel)**
    *   **獨立結帳畫面**: 從點餐頁面進入專屬結帳畫面，清晰列出所有費用明細。
    *   **費用明細**: 自動計算小計、折扣、服務費、稅金，並顯示最終應付總額。
    *   **手動折扣**: 支援輸入固定金額或百分比折扣，並可填寫折扣原因。
    *   **自動折扣**: 系統可根據預設規則（如：滿額折、買一送一）自動套用優惠。

2.  **多樣化支付方式 (Multiple Payment Methods)**
    *   **現金支付**: 內建現金計算機，快速計算找零金額。
    *   **電子支付**: 支援多種行動支付方式（如：LINE Pay, JKO Pay 等），方便記錄。
    *   **外送平台支付**: 自動對應 Foodpanda、Uber Eats 等已付款訂單。
    *   **招待單結帳**: 內部招待訂單可直接以「招待」方式結帳，不計入營收。

3.  **硬體整合 (Hardware Integration)**
    *   **錢箱控制**: 結帳完成後可自動發送指令開啟錢箱。
    *   **收據列印**: 自動或手動列印交易收據，支援多種模板。
    *   **優惠券列印**: 滿足特定條件（如：消費滿額）時，可自動列印優惠券供顧客下次使用。

### 三、 廚房與出餐管理 (Kitchen & Fulfillment)

1.  **KDS (廚房顯示系統 - Kitchen Display System)**
    *   **即時訂單顯示**: 訂單儲存後，即時顯示在 KDS 畫面上，按時間排序。
    *   **訂單狀態追蹤**: 廚房人員可將已備妥的訂單標示為「備餐完成」，狀態同步回桌位圖。
    *   **清晰的品項列表**: 每張訂單卡片清晰展示品項、數量、客製化選項與備註。
    *   **時間追蹤**: 顯示每張訂單的等待時間，並以顏色區分（如：超過10分鐘變黃色，超過20分鐘變紅色），提醒優先處理。

2.  **多站點出單 (Multi-Station Printing)**
    *   **智慧分單**: 可設定不同產品分類（如：冷飲、熱食、炸物）對應到不同的出單機（如：吧台機、廚房機）。
    *   **標籤列印**: 支援為每個品項（特別是手搖飲）列印詳細的標籤貼紙，包含品名、客製化選項、訂單號等資訊。
    *   **網路與藍牙支援**: 支援 IP 網路印表機和藍牙印表機，部署彈性高。

### 四、 後台管理與設定 (Backend Management & Settings)

1.  **產品管理 (Product Management)**
    *   **新增/編輯產品**: 設定產品名稱、價格、所屬分類、排序、圖片等。
    *   **客製化模板**: 建立可重複使用的客製化模板（如：甜度、冰塊），並將其應用於單一產品或整個分類。
    *   **套餐設定**: 組合多個單品成為套餐，並設定子項目的規則。
    *   **平台定價**: 可為不同外送平台設定獨立的售價。
    *   **批量新增**: 支援透過特定格式的文字輸入，一次性快速新增多個產品。

2.  **員工與權限管理 (Employee & Permission Management)**
    *   **角色系統**: 內建店長、經理、收銀員等角色，並可自訂各角色的操作權限。
    *   **PIN 碼登入**: 每位員工使用專屬 PIN 碼登入及操作，確保權責分明。
    *   **打卡功能**: 員工可進行上下班打卡，系統自動記錄工時。
    *   **薪資管理**: 支援時薪、日薪、月薪制，可快速計算薪資報表。

3.  **店家設定 (Store Settings)**
    *   **基本資訊**: 設定店名、地址、聯絡電話、Logo。
    *   **營業時間**: 設定一週七天的詳細營業時段。
    *   **外觀與佈景**: 自訂系統主色調、背景顏色、UI 元件大小，打造專屬風格。
    *   **貨幣設定**: 設定貨幣代碼與符號。
    *   **訂單號碼規則**: 自訂內用、外帶、外送平台的訂單起始與結束號碼。

4.  **印表機與模板管理 (Printer & Template Management)**
    *   **多印表機設定**: 可設定多達四台印表機（收據、標籤、出單站1、出單站2），並分別指定其連接方式（藍牙/IP）與紙張寬度。
    *   **模板編輯器**:
        *   **圖像模式**: 拖放式的視覺化編輯器，可自由設計收據、標籤、優惠券的版面，包含文字、Logo、QR Code、線條等元素。
        *   **文字模式**: 針對傳統 ESC/POS 指令印表機，提供基於文字的格式設定，控制字體大小、對齊、粗體等。
    *   **自動列印規則**: 可根據訂單類型（內用、外帶、外送）設定是否自動列印收據和標籤。

### 五、 報表與數據分析 (Reports & Analytics)

1.  **日結報表 (Daily Closing Report)**
    *   **營業總覽**: 顯示總銷售額、訂單數、客單價、人均消費等關鍵指標。
    *   **支付方式統計**: 依現金、各類行動支付等方式分類匯總銷售額與訂單數。
    *   **產品銷售排行**: 列出熱銷商品及其銷售數量與金額。
    *   **現金帳務核對**: 包含期初現金、現金收入、現金支出、應有現金與實際盤點現金的差異分析。
    *   **報廢與招待統計**: 匯總當日的報廢與招待總金額。
    *   **報表列印**: 可將完整的日結報表列印出來。

2.  **歷史訂單查詢 (Historical Orders)**
    *   **多條件篩選**: 可依日期範圍、訂單類型（內用、外帶等）、關鍵字（訂單號、桌號、品項名稱）進行查詢。
    *   **訂單詳情查看**: 點擊單筆訂單可查看完整內容，包含所有品項、客製化選項、付款資訊及操作人員。
    *   **操作功能**: 支援對已結帳訂單進行作廢、轉招待或重新列印單據等操作（需權限）。

3.  **進階報表 (Advanced Reports)**
    *   **多店報表**: (需權限) 跨分店營業數據比較，一覽各分店的營運表現。
    *   **薪資報表**: 根據員工打卡記錄與薪資設定，自動計算指定時間範圍內的薪資總額。

### 六、 系統與技術特性 (System & Technical Features)

1.  **離線優先設計 (Offline-First)**
    *   **本地資料庫**: 使用 Isar 在設備端儲存操作記錄。
    *   **操作隊列**: 所有在離線狀態下的操作（點餐、結帳、新增品項等）都會被安全地儲存在本地隊列中。
    *   **自動同步**: 一旦網路恢復連線，系統會自動將本地隊列中的操作同步至雲端 Firebase 資料庫。

2.  **跨平台支援 (Cross-Platform)**
    *   基於 Flutter 開發，核心程式碼可運行於 Android、iOS、Web 等多個平台（目前主要針對 Android 平板進行優化）。

3.  **安全性 (Security)**
    *   **角色權限**: 嚴格的權限劃分，防止未經授權的操作。
    *   **操作日誌**: 系統會記錄關鍵操作（如：作廢、折扣、日結），便於追溯。
    *   **雲端數據**: 所有資料儲存在安全的 Firebase 雲端，防止本地設備損壞導致的數據遺失。
  
### 📂 專案結構 (Project Structure)

本專案遵循功能導向的分層架構，將 UI、狀態管理、業務邏輯和資料模型清晰地分開，以便於維護和擴展。

```
jcxpos/
├── .github/workflows/      # GitHub Actions CI/CD 工作流程設定
│   ├── release-apk.yml       # (私有庫) 當推送到 main 分支時，建置並簽署 APK，建立 GitHub Release
│   └── build-and-release.yml # (公有庫) 當私有庫更新時，建置 APK 並發布到公有庫
│
├── android/                # Android 原生平台特定程式碼
│   ├── app/                  # Android 應用程式模組
│   │   ├── build.gradle.kts    # Android 應用程式的 Gradle 建置腳本 (Kotlin DSL)
│   │   ├── build.gradle        # (備用) Groovy 版本的 Gradle 建置腳本
│   │   └── src/main/
│   │       ├── java/com/eiviayw/library/ # 核心原生繪圖函式庫
│   │       │   ├── bean/                 # 繪圖資料模型 (Data Beans)
│   │       │   │   ├── element/          # 基礎繪圖元素 (Element)
│   │       │   │   │   ├── BaseElement.kt      # 所有繪圖元素的基底類別，定義位置、大小等
│   │       │   │   │   ├── GraphicsElement.kt  # 點陣圖 (Bitmap) 元素
│   │       │   │   │   ├── LineElement.kt      # 實線元素
│   │       │   │   │   ├── LineDashedElement.kt# 虛線元素
│   │       │   │   │   └── TextElement.kt      # 文字元素
│   │       │   │   └── param/            # 從 Flutter 接收的參數物件 (Parameter)
│   │       │   │       ├── BaseParam.kt        # 所有參數物件的基底類別
│   │       │   │       ├── GraphicsParam.kt    # 點陣圖參數
│   │       │   │       ├── LineParam.kt        # 實線參數
│   │       │   │       ├── LineDashedParam.kt  # 虛線參數
│   │       │   │       ├── MultiElementParam.kt# 多元素水平排列的參數
│   │       │   │       └── TextParam.kt        # 文字參數
│   │       │   ├── draw/                 # 繪圖核心邏輯
│   │       │   │   ├── BitmapOption.kt     # 畫布設定，如寬高、邊距、對齊方式
│   │       │   │   ├── DrawBitmapHelper.kt # 主要繪圖輔助類別，將 Param 轉換為 Element 並協調繪製
│   │       │   │   └── Drawing.kt          # 實際在 Android Canvas 上執行繪圖操作的類別
│   │       │   ├── provide/              # (未使用) 繪圖庫的提供者基底類別
│   │       │   └── util/                 # 繪圖庫的工具類
│   │       │       ├── BitmapUtils.kt      # 點陣圖處理工具 (縮放、裁切、轉換)
│   │       │       └── SerializationUtils.kt # 序列化工具 (深拷貝)
│   │       │
│   │       └── kotlin/com/jcxtech/jcxpos/ # 專案主要原生程式碼
│   │           ├── BluetoothPrinterManager.kt # 核心藍牙印表機管理，處理連接、斷開、發送資料、獲取狀態
│   │           └── MainActivity.kt            # Flutter 應用程式的 Android 入口，處理 MethodChannel 和 EventChannel 通訊
│   │
│   ├── build.gradle.kts      # Android 專案層級的 Gradle 建置腳本
│   ├── gradle.properties     # Gradle JVM 和 AndroidX 相關設定
│   ├── key.properties        # (本地) 應用程式簽署憑證的密碼和別名 (不應提交至 Git)
│   ├── local.properties      # (本地) Flutter SDK 和 Android SDK 的路徑
│   └── settings.gradle.kts   # Gradle 專案設定，定義包含哪些模組
│
├── lib/                      # Flutter 應用程式的主要 Dart 程式碼
│   ├── models/               # 資料模型 (Data Models) - 定義應用程式的核心資料結構
│   │   ├── action_log.dart     # 操作日誌的資料模型
│   │   ├── category.dart       # 產品分類的資料模型
│   │   ├── common_expense.dart # 常用支出的資料模型
│   │   ├── common_waste_reason.dart # 常用報廢原因的資料模型
│   │   ├── coupon_template.dart# 優惠券模板的資料模型
│   │   ├── daily_closing.dart  # 日結紀錄的資料模型
│   │   ├── discount.dart       # 折扣規則的資料模型
│   │   ├── employee.dart       # 員工、角色、薪資的資料模型
│   │   ├── expense.dart        # 單筆支出紀錄的資料模型
│   │   ├── ingredient.dart     # 庫存原料的資料模型
│   │   ├── inventory_log.dart  # 庫存異動日誌的資料模型
│   │   ├── local_log.dart      # 本地 Isar 日誌的資料模型
│   │   ├── offline_operation.dart # 本地 Isar 離線操作的資料模型
│   │   ├── order.dart          # 訂單、訂單品項、已套用折扣的結構與邏輯
│   │   ├── payment_method_type.dart # 支付方式枚舉與本地化
│   │   ├── product.dart        # 產品、客製化選項、套餐、配方的結構
│   │   ├── RestaurantTable.dart# 桌位及其狀態的資料模型
│   │   ├── template_model.dart # 圖像式列印模板的結構 (視覺化編輯器)
│   │   ├── text_format_template.dart # 文字式列印模板的結構 (ESC/POS)
│   │   ├── tutorial_step.dart  # 教學引導步驟的資料模型
│   │   └── wasted_item.dart    # 報廢品項紀錄的資料模型
│   │
│   ├── providers/            # 狀態管理 (State Management) - 使用 Provider 模式
│   │   ├── category_provider.dart # 管理產品分類的讀取、新增、修改、刪除
│   │   ├── discount_provider.dart # 管理折扣規則
│   │   ├── employee_provider.dart # 管理員工登入狀態、權限驗證、打卡紀錄
│   │   ├── expense_provider.dart  # 管理支出相關操作 (常用支出、單筆支出)
│   │   ├── inventory_provider.dart# 管理庫存原料與庫存調整邏輯
│   │   ├── order_provider.dart    # 核心！管理訂單狀態，包括開桌、點餐、結帳、離線隊列等
│   │   ├── pos_provider.dart      # 管理 POS 硬體與 UI 相關設定 (印表機狀態、UI 縮放)
│   │   ├── product_provider.dart  # 管理產品列表的載入與快取
│   │   ├── settings_provider.dart # 管理店家全域設定，如店名、印表機配置、UI主題等
│   │   ├── table_provider.dart    # 管理桌位列表的讀取與狀態更新
│   │   └── tutorial_provider.dart # 管理教學引導的狀態
│   │
│   ├── screens/              # UI 頁面 (Screens/Views) - 應用程式的各個主要介面
│   │   ├── home_screen.dart         # 主選單頁面
│   │   ├── splash_screen.dart       # 啟動畫面，負責初始化
│   │   ├── login_screen.dart        # 員工登入頁面
│   │   ├── initial_setup_screen.dart# 首次使用或恢復店家設定的頁面
│   │   ├── table_status_screen.dart # 桌位狀態總覽頁面
│   │   ├── order_item_selection_screen.dart # 核心點餐頁面
│   │   ├── individual_checkout_screen.dart # 獨立結帳頁面
│   │   ├── daily_report_screen.dart # 日結報表頁面
│   │   ├── historical_orders_screen.dart # 歷史訂單查詢頁面
│   │   ├── kds_screen.dart          # 廚房顯示系統 (KDS) 頁面
│   │   ├── clock_in_out_screen.dart # 員工打卡頁面
│   │   ├── coupon_print_screen.dart # 手動列印優惠券頁面
│   │   ├── system_info_screen.dart  # 系統資訊與說明頁面
│   │   ├── waste_item_selection_screen.dart # 報廢品項選擇頁面
│   │   ├── template_editor_screen.dart # 圖像式模板編輯器頁面
│   │   ├── template_list_screen.dart   # 圖像式模板列表頁面
│   │   ├── auth_expired_screen.dart # 授權過期提示頁面
│   │   ├── reports/                 # 報表相關頁面
│   │   │   ├── reports_screen.dart        # 報表主選單
│   │   │   ├── multi_store_report_screen.dart # 多店報表頁面
│   │   │   └── payroll_report_screen.dart   # 薪資報表頁面
│   │   └── settings/                # 所有設定相關的子頁面
│   │       ├── settings_screen.dart       # 設定主頁面 (包含多個 Tab)
│   │       ├── product_setting_screen.dart# 產品列表管理頁面
│   │       ├── product_edit.dart          # 新增/編輯單一產品的頁面
│   │       ├── category_management_screen.dart # 分類管理頁面
│   │       ├── table_setting_screen.dart  # 桌位與區域管理頁面
│   │       ├── business_hours_screen.dart # 營業時間設定頁面
│   │       ├── employee_management_screen.dart # 員工管理頁面
│   │       ├── permission_settings_screen.dart # 角色權限設定頁面
│   │       ├── printer_settings_screen.dart  # 印表機與列印相關設定頁面
│   │       ├── product_customization_template_screen.dart # 客製化選項模板管理頁面
│   │       ├── discount_management_screen.dart # 折扣規則管理列表頁面
│   │       ├── discount_edit_screen.dart     # 新增/編輯折扣規則頁面
│   │       ├── branch_management_screen.dart # 分店關聯管理頁面
│   │       ├── inventory_management_screen.dart # 庫存原料管理頁面
│   │       ├── log_viewer_screen.dart        # 本地日誌查看器
│   │       ├── bulk_product_add_screen.dart  # 批量新增產品頁面
│   │       ├── common_expense_management_screen.dart # 常用支出項目管理
│   │       ├── common_waste_reason_management_screen.dart # 常用報廢原因管理
│   │       ├── text_print_format_screen.dart # 文字式列印模板編輯器
│   │       ├── admin_store_management_screen.dart # (系統管理員) 店家管理頁面
│   │       └── admin_store_auth_screen.dart  # (系統管理員) 店家授權管理頁面
│   │
│   ├── services/             # 業務邏輯與服務 (Business Logic & Services)
│   │   ├── drawing_service.dart     # 透過 MethodChannel 呼叫原生繪圖功能的 Dart 介面
│   │   ├── isar_service.dart        # 在 Mobile 平台上使用 Isar 實現本地儲存
│   │   ├── log_service.dart         # 本地日誌記錄服務 (條件導出)
│   │   ├── log_service_mobile.dart  # Mobile 平台的日誌實現 (使用 Isar)
│   │   ├── log_service_web.dart     # Web 平台的日誌空實現
│   │   ├── log_service_stub.dart    # 日誌服務的空殼，用於非 Web/Mobile 平台
│   │   ├── log_upload_service.dart  # 上傳日誌到 Firebase Storage 的服務
│   │   ├── offline_storage_service.dart # 抽象化的本地儲存服務介面
│   │   ├── printing_service.dart    # 核心列印服務，協調模板與原生指令
│   │   ├── report_service.dart      # 產生多店報表的服務
│   │   ├── storage_service.dart     # 本地儲存服務的工廠 (條件導出)
│   │   ├── storage_service_mobile.dart # Mobile 平台的儲存服務工廠
│   │   ├── storage_service_web.dart    # Web 平台的儲存服務工廠
│   │   ├── storage_service_stub.dart   # 儲存服務的空殼
│   │   ├── template_service.dart    # 管理列印模板的讀取、儲存與預設值
│   │   ├── update_service.dart      # 應用程式版本更新檢查服務
│   │   └── web_storage_service.dart   # Web 平台的本地儲存空實現
│   │
│   ├── widgets/              # 可重用的 UI 元件 (Reusable UI Components)
│   │   ├── add_expense_dialog.dart    # 新增支出對話框
│   │   ├── cash_calculator_dialog.dart# 現金盤點計算機對話框
│   │   ├── common_app_bar.dart      # 應用程式的通用頂部導航欄
│   │   ├── customization_dialog.dart  # 產品客製化選項選擇對話框
│   │   ├── feedback_snackbar.dart   # 統一風格的提示訊息框
│   │   ├── item_selection_dialog.dart # 選擇要列印標籤的品項對話框
│   │   ├── numpad.dart              # 數字鍵盤元件
│   │   ├── reprint_options_dialog.dart# 重新列印選項對話框
│   │   ├── start_new_day_dialog.dart  # 開啟新營業日對話框
│   │   ├── table_widget.dart        # 單個桌位的 UI 元件
│   │   └── tutorial_overlay.dart    # 教學引導的覆蓋層 UI
│   │
│   ├── l10n/                   # 本地化與多國語言 (Localization & i18n)
│   │   ├── app_en.arb             # 英文語系資源檔
│   │   └── app_localizations.dart # Flutter 自動產生的本地化代理類別
│   │
│   ├── utils/                  # 工具類 (Utilities)
│   │   ├── debouncer.dart         # 用於延遲執行操作，防止頻繁觸發 (如搜尋)
│   │   └── settings_manager.dart  # 管理本地裝置偏好設定 (如列印模式)
│   │
│   ├── firebase_options.dart   # Firebase 初始化設定檔 (由 FlutterFire CLI 自動產生)
│   └── main.dart               # 應用程式進入點 (App Entry Point)
│                                 # 負責初始化 Firebase、Provider、設定路由等
│
├── assets/                   # 靜態資源 (Static Assets)
│   └── images/
│       └── logo.png            # 應用程式 Logo
│
├── l10n.yaml                 # 本地化工具的設定檔
├── analysis_options.yaml     # Dart 分析器與 Linter 的規則設定
└── pubspec.yaml              # 專案依賴與設定檔
                              # 定義 Flutter 版本、專案名稱、第三方套件等
```

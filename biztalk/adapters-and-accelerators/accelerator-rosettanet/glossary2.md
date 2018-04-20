---
title: RosettaNet 加速器，BizTalk Server 中的詞彙 |Microsoft 文件
description: 一般詞彙和定義必須知道並了解如何使用 BizTalk Accelerator for RosettaNet
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d98a5ed4-adc5-4ca9-b9d9-38ab02a0bda6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd89d75b0d36359fcf59f7edae0bb950a7196ca7
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="glossary"></a>詞彙
[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 使用下列字彙術語和定義。  

  
## <a name="a"></a>只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，  
 **應用程式配接器**  
 實作應用程式配接器介面的應用程式。 對於內送動作訊息 (要求或回應) 之認可的通知機制，會叫用應用程式配接器。 它會實作兩種方法：`BeginNotify`和`EndNotify`。 公用回應者會叫用 `BeginNotify` 方法，而現成的私用回應者則會叫用 `EndNotify` 方法。 只要呼叫 `Notify` 方法，就表示訊息已經成功儲存到 MessagesToLOB 資料表中。  
  
 **動作 URL**  
 要為主要組織傳輸動作訊息在非同步的過程中，例如，交易夥伴 URL http://FabrikamServer/BTARNApp/RNIFReceive.aspx。  
  
## <a name="b"></a>B  
 **BizTalk Accelerator for RosettaNet**  
 BizTalk Server，可協助組織建立與 RosettaNet 實作架構 (RNIF) 的附加產品-相容解決方案。  
  
 **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 系統管理**  
 可讓您描述程序範本及管理交易夥伴協議的 Microsoft [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 應用程式。  
  
 **BizTalk 編輯器**  
 可以用來建立、編輯和管理規格的工具。 您可以使用 BizTalk 編輯器，根據規格範本、現有的結構描述、特定類型的文件執行個體，或是空白規格來建立規格。  
  
 **BizTalk 協調流程設計師**  
 設計工具，可以用來建立描寫長時間執行、偶合鬆散以及可執行之商務程序的繪圖。 XLANG 排程繪圖是在您用來執行自動化的商務程序的 XLANG 排程中編譯。  
  
 **BizTalk Server**  
 商務程序自動化和應用程式整合中及企業間之 Microsoft 產品。 BizTalk Server 提供功能強大的 Web 架構開發和執行環境，可整合鬆散偶合、 長時間執行商務程序，和企業之間。  
  
 BizTalk Server 功能包括新的和現有的 XLANG 排程; 組合在現有的應用程式; 之間的整合文件規格和規格轉換，定義監視和執行階段活動的記錄。  
  
 這個伺服器會提供標準的閘道，經由網際網路傳送和接收文件，並提供許多服務，幫助確認資料的完整性、傳遞性、安全性以及對 BizTalk Framework 和其他重要文件格式的支援。  
  
 **BtarnClean**  
 清除電腦中 BTARN 成品的公用程式。  
  
 **商務動作**  
 含有商務內容的 RosettaNet 訊息，例如訂單要求或報價要求。 配合商務信號，這些動作便會產生所需的項目，以便完成特定「交易夥伴介面程序 (PIP)」所指定的商務活動。  
  
 **商務活動監控 (BAM)**  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 的功能，用來提供商務使用者對於異質商務程序的即時檢視， 以便進行重要的商務決策。  
  
 **商務信號**  
 在兩個 RosettaNet 網路應用程式之間進行交換的 RosettaNet 訊息 (像是 ReceiptAcknowledgement 或例外狀況)，用來在執行 PIP 執行個體時，溝通特定的事件。 配合商務動作，這些信號便會產生所需的項目，以便完成特定 PIP 所指定的商務活動。  
 
  
## <a name="c"></a>C  
 **CertWizard**  
 用來從 .pfx (.p12) 或 .cer (.der) 檔案，將簽章或加密憑證匯入私用或公用儲存區，以便與 BTARN 搭配使用的公用程式。 由於具有用於解密或簽章的私密金鑰，.pfx 檔 (也就是個人資訊交換 – PKCS #12) 通常都會由密碼加以保護。 .cer 檔 (憑證檔) 則具有公開金鑰，用來進行簽章的加密和驗證。  
  
 **化學資料交換 (CIDX) Chem eStandards**  
 資料交換的統一標準，為了用於化學藥品的買賣交易和運送而特別開發。 這些標準是以普遍能接受辨識的電子資料交換標準—XML 為基礎。 BTARN 能支援 CIDX Chem eStandards。  
  
 **叢集**  
 高層級的商務程序群組，例如訂單管理、存貨管理或服務與支援。 RosettaNet 所處理的叢集能顯示出供應鏈產業的核心商務程序。  
  
## <a name="d"></a>D  
 **數值資料通用編號系統 (A-U-N-S)**  
 循序產生的九位數編號，可以獨一無二地識別全球企業的位置。  
  
 **傳遞標頭**  
 RosettaNet 訊息的一部分。 傳遞標頭是能識別訊息傳送者、收件者和訊息執行個體資訊的 XML 文件。  
  
 **目的地組織**  
 在傳訊連接埠中，指定用來做為文件傳送目的地的組織。  
  
 **數位演算法**  
 採用訊息做為輸入，並產生該訊息之雜湊或摘要的演算法，根據訊息內容的不同，具有固定長度，且類型極為複雜的位元組。 這種演算法的設計準則，就是要讓任何人都難以偽造摘要；或是難以在不變更摘要的情況下變更其訊息。 在訊息驗證和數位簽章配置中的應用程式，通常都會使用摘要演算法。 廣泛使用的演算法包括 MD5 和 SHA1。 對於內送訊息，BTARN 支援 MD5 和 SHA1；對於外寄訊息，則只支援 SHA1。  
  
 **文件定義**  
 表示特定文件的屬性集。 文件定義屬性包括文件規格的指標，並且可以包含全域追蹤欄位和選取準則。  
  
 **文件執行個體**  
 傳送至 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 之實際資料的表示法。 文件執行個體和文件規格不同處在於，規格會定義資料的結構，而文件執行個體則是包含在結構中之特定資料的表示法。  
  
 **文件類型定義 (DTD)**  
 用來指定其他項目和屬性中，所要顯示的項目和屬性，以及指定這些項目和屬性之順序、發生頻率和內容之條件約束的標準定義。  
  
 **雙向動作交易**   
 啟動者傳送要求動作、接收信號，然後回應者發生回應動作的程序。 啟動者傳送信號至回應動作，即完成該程序。  
  
## <a name="e"></a>E  
 **可延伸標記語言 (XML)**  
 由全球資訊網協會 (W3C) 所開發的規格，讓程式設計人員能建立超越標準 HTML 功能的自訂標籤。 當 HTML 只能使用預先定義的標籤，描述頁面中的項目時，XML 卻能讓網頁開發人員自行定義標籤。 對於任何虛擬的資料項目 (例如產品或到期金額)，標籤都可以針對特定的應用程式來使用。 這讓網頁也可以具有和資料庫記錄相同的功能。  
  
 **可延伸樣式表語言 (XSL)**  
 用於 XML 文件的樣式表格式。 XSL 用來定義 XML 的顯示，就像階層式樣式表 (CSS) 用來定義 HTML 的顯示。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 使用 XSL 當做翻譯語言，這兩種規格之間。  
  
## <a name="g"></a>G  
 **全球商務識別碼 (GBI)**  
 用來識別交易合作對象的唯一識別碼。 RosettaNet 會使用九位數的鄧白氏編號系統 (DUNS，Dun and Bradstreet Numbering System) 做為 GBI。  
  
## <a name="h"></a>H  
 **主要組織**   
 用來識別您的組織之別名。  
  
## <a name="i"></a>I  
 **起始端**  
 首先對交易夥伴引發程序的交易或通知程序中，組織所扮演的角色。  
  
## <a name="l"></a>L  
 **企業營運 (LOB) 應用程式**  
 做為後端系統，用來與 BTARN 進行溝通的應用程式。  
  
 **回送公用程式**  
 供程式開發人員用來自動產生回送協議 (組織對夥伴協議的鏡像複本) 的公用程式。 這讓您可以在單一電腦上，執行組織對夥伴以及夥伴對組織的訊息交換。  
  
## <a name="m"></a>M  
 **對應**  
 在一規格中的記錄和欄位以及其他規格中的記錄和欄位之間，定義對應關係的 XML 檔案。 對應含有 XSL 樣式表，讓 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 用來執行該對應中描述的轉換資訊。 對應是建立於 BizTalk 對應工具中。
  
 **我的組織**  
 會在交易夥伴協議中顯示您的組織。   
  
 **多用途網際網路郵件延伸 (標準 MIME)**  
 可讓您的網際網路電子郵件通訊協定的延伸模組會使用通訊協定交換不同種類的網際網路上的資料檔案： 音訊、 視訊、 影像和應用程式。  
  
## <a name="n"></a>N  
 **不可否認性**  
 用來確認訊息傳送者不能在訊息傳送後，否認傳送過這個訊息，而收件者也不能否認接收過這個訊息的方式。 內送訊息的不可否認功能需要收件者儲存訊息，而訊息也必須具有使用傳送者之簽章憑證的數位簽章，確保其正確性。 外寄訊息的不可否認功能則需要儲存認可訊息 (來自第一個訊息之收件者的內送訊息)，而訊息也必須具有使用收件者之簽章憑證的數位簽章 (原始訊息之摘要的簽章)。   
  
 **通知**  
 啟動者以單一訊息通知回應者的 RNIF 1.1 程序類型。 回應者必須要以商務信號做為認可來回應。  
  
 **失敗 (PIP 0A1) 的通知**  
 指出未預期之程序錯誤的 PIP。 不管是啟動者或是回應者，都可以發出失敗通知。 它可以針對現有或是之前所交換的程序。 根據收到的 0A1，接收合作對象即可確認所參考的程序會視為無效。  
  
## <a name="o"></a>O  
 **組織**  
 可以主導商務交易的交易夥伴或是業務單位。  
  
## <a name="p"></a>P  
 **封裝**  
 將 RosettaNet 訊息與其 XML 呈現方式互相轉換的程序。  
  
 **交易夥伴介面程序 (PIP)**  
 PIP 會描述詳細的商務文件和協議集，其中包含文件的詳細內容。  
  
 **PIP 規格文件**  
 包含關於在 BTARN 管理主控台中建立程序組態時，所需設定的指導文件。 您可以從 RosettaNet 組織 (RosettaNet.org) 下載 PIP 規格文件和該 PIP。包含關於在 BTARN 管理主控台中建立程序組態時，所需設定的指導文件。 您可以從 RosettaNet 組織 (RosettaNet.org) 下載 PIP 規格文件和該 PIP。  
  
 **前序標頭**  
 XML 節點，能識別與商務訊息相容之標準的名稱和版本。 它會與其他標頭一起進行封裝，以便形成完整的 RosettaNet 訊息。 這也稱為前序。  
  
 **私用程序**   
 組織內部的商務程序。 BTARN 會實作私用程序，做為長期執行的 BizTalk 協調流程。  
  
 **處理序組態設定 (PCS) 設定檔**  
 決定交易夥伴協議執行的方式。 使用 PCS 設定檔，便能輸入 RosettaNet「交易夥伴介面程序 (PIP)」的詳細組態設定。 所有在 RosettaNet PIP 規格中指定的組態設定值，都會對應到 PCS 設定檔中的某個項目。 因此，您可以使用一個 PCS 設定檔，處理多項交易夥伴協議。  
  
 **port**  
 使用特定實作方式的具名位置。 在「BizTalk 協調流程設計師」中，連接埠是由傳送或接收訊息的位置以及用來實作通訊動作的技術加以定義。 這個位置只會由這個連接埠的名稱唯一識別。  
  
 **公開程序**   
 包含與交易夥伴進行整合成為公開程序的商務程序。 BTARN 會實作公開程序，做為長期執行的 BizTalk 協調流程。 一個公開程序協調流程會在啟動者端執行，另一個則是在回應者端執行。 BTARN 安裝程式為 RNIF 1.1 與 RNIF 2.01 都提供了啟動者及回應者公開程序協調流程版本。 這些公開程序協調流程會實作所有的 RNIF 程序。 公開程序對其餘的元件隱藏了 RNIF 的複雜性。 這種公開程序除了強制與 RNIF 相容的訊息流程之外，也決定了預設追蹤設定，並提供執行階段的程序狀態資訊。  
  
## <a name="r"></a>R  
 **回應者**  
 在交易或通知程序中回應交易夥伴之要求的組織角色。  
  
 **RosettaNet 實作架構 (RNIF)**  
 對於想要建立能執行 PIP，且可互相合作之軟體應用程式元件的公司，提供他們實作指導的標準架構。  
  
 **RosettaNet 訊息**  
 包含前序標頭、傳遞標頭 (就 RNIF 2.0 而言)、服務標頭和服務內容的邏輯群組。  
  
 **RosettaNet 物件**  
 包裝後要以 RosettaNet 實作架構 1.1 版之格式進行傳送的 RosettaNet 訊息。  
  
## <a name="s"></a>S  
 **schema**  
 XML 檔案結構的定義。 結構描述包含有屬性資訊，就像它屬於結構中的記錄和欄位一樣。  
  
 **服務內容**  
 RosettaNet 訊息的主要元件。 它是一個 XML 節點，表示特定 PIP 所指定的商務內容。  
  
 **服務標頭**  
 用來識別與商務訊息有關部分的 XML 文件，這些部分包括 PIP、商務活動和動作、傳送和接收服務、交易夥伴，以及角色。  
  
 **信號 URL**  
 主要組織傳輸信號訊息的目標 URL。 例如， http://FabrikamServer/BTARNApp/RNIFReceive.aspx。  
  
 **單向動作通知**  
 啟動者傳送單一動作訊息，然後回應者以訊息進行回覆的程序。  
  
 **規格**  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 特有的 XML 結構描述。 您可以在 BizTalk 編輯器中，根據產業標準 (例如 EDIFACT、X12 和 XML) 或一般檔案 (分隔資料、位置資料，或是分隔和位置資料) 建立規格。 BizTalk 對應工具會使用規格建立對應，這些規格和來源規格以及目的規格一樣都屬於開放式。  
  
 **同步 URL**  
 主要組織會使用來建立與夥伴，例如，同步交易的 URL http://FabikamServer/BTARNApp/RNIFReceive.aspx。  
  
 **同步交易**  
 啟動者在相同的 HTTP 狀態傳回回應 (雙向動作) 或信號 (單向動作)，而不關閉連線的程序。  
  
## <a name="t"></a>T  
 **交易夥伴**  
 與您的組織交換電子資料的外部組織。  
  
 **交易夥伴協議**  
 您的組織與交易夥伴之間的協議。 交易夥伴協議會參考「程序組態設定」設定檔、主要組織和交易夥伴，並包含協議特殊的組態設定。  
  
 **交易**  
 啟動者傳送 RosettaNet 訊息、接收信號、接收 RosettaNet 訊息做為回答，以及傳送認可信號的 RNIF 1.1 程序。  
  
## <a name="v"></a>V  
 **驗證配接器**  
 實作驗證配接器介面的應用程式。 當公開回應者收到動作訊息 (要求或回應) 時，便會叫用「驗證配接器」。 它可以包含企業在接受內送訊息前，所需的任何驗證規則集。 BTARN 本身就會在接收管線和公用協調流程中執行驗證。  
  
## <a name="x"></a>X  
 **XLANG 排程**  
 用來描述商務程序與後端整合的特定 XML 語言。 BTARN 中的特定商務程序會以 XLANG 語言加以表示。 XLANG 排程是以 .skx 做為副檔名進行儲存。  
  

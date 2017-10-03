---
title: "SWIFT 加速器，BizTalk Server 中的詞彙 |Microsoft 文件"
description: "一般詞彙和定義必須知道並了解如何使用 BizTalk Accelerator for SWIFT"
ms.custom: 
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7331beb-f6a7-4eea-8b31-28f5d15666d0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1230b6b1578a4a3aa7c719df4dffb718b0c748e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="glossary"></a>詞彙
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for SWIFT 使用下列字彙術語和定義。  
  
## <a name="a"></a>只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，  
 **組譯工具**  
 A [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 「 組合 」 階段的輸出管線處理期間叫用的傳送管線元件。 組譯工具通常會序列化傳出訊息從 XML 到某些一般檔案格式的工作。  
  
 **組件**  
 主要建置組塊的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)]應用程式。 它是重複使用、 版本、 安全性和部署的基本單位。 它是顯示程式設計人員必須是單一動態連結程式庫 (DLL) 或可執行檔 (EXE) 的檔案集合。  
  
 **組件快取**  
 用來儲存組件來並行整部機器的程式碼快取。 有兩個部分快取。 全域組件快取包含明確安裝在電腦上的許多應用程式之間共用的組件。 下載快取會儲存從網際網路下載的程式碼或內部網路網站、 隔離的應用程式，以便代表一個應用程式下載程式碼，觸發下載或頁面不會影響其他應用程式。  
  
## <a name="b"></a>B  
 **Bank 識別項代碼 (BIC)**  
 SWIFT 所定義，用來識別金融機構中，程式碼。  
  
 **商務規則編輯器 」 工具**  
 用來編寫原則的圖形使用者介面工具。  
  
 **商務規則引擎 (BRE)**  
 根據事實評估規則，並依照其評估結果啟始動作的執行階段推斷引擎。  
  
## <a name="c"></a>C  
 **條件式規則**  
 規則，指定 SWIFT 訊息類型的欄位間的關聯性。 SWIFT 標準版本指南中，可定義條件式規則。  
  
## <a name="d"></a>D  
 **反組譯工具**  
 A[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收管線元件處理輸入的管線的解譯階段期間所叫用。 解譯器 」 通常會從某些一般檔案格式的輸入的訊息剖析成 XML 的作業。  
  
## <a name="e"></a>E  
 **錯誤碼**  
 程式碼，其中包含字母，後面接著兩個數字，指出特定訊息類型的規則的違規情形。  
  
 **可延伸標記語言 (XML)**  
 由全球資訊網協會 (W3C) 所開發的規格，讓程式設計人員能建立超越標準 HTML 功能的自訂標籤。 HTML 會使用只有預先定義的標記來描述頁面內的元素，而 XML 可讓網頁的開發人員所定義的標籤。 對於任何虛擬的資料項目 (例如產品或到期金額)，標籤都可以針對特定的應用程式來使用。 這讓網頁也可以具有和資料庫記錄相同的功能。  
  
 **可延伸樣式表語言 (XSL)**  
 可延伸標記語言 (XML) 文件的樣式表格式。 XSL 用來在相同的方式，該階層式樣式表 (CSS) 用來定義顯示的超文字標記語言 (HTML) 中定義的 XML 顯示。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用 XSL 當做翻譯語言，這兩種規格之間。  
  
## <a name="f"></a>F  
 **FIN**  
 財務 SWIFT 已定義的結構描述和驗證標準 SWIFT 標準版指南 2003年中的訊息。  
  
## <a name="g"></a>G  
 **全域組件快取 (GAC)**  
 整個電腦的程式碼快取，它會存放供電腦上多個應用程式共用而特別安裝的組件。 在全域組件快取中部署的應用程式必須具有強式名稱。  
  
## <a name="h"></a>H  
 **使用安全超文字傳輸通訊協定 (HTTPS)**  
 超文字傳輸通訊協定 (HTTP) 使用安全通訊端層 (SSL) 加密通訊協定。  
  
## <a name="i"></a>I  
 **交換**  
 完整的訊息，用來組成較小的訊息部分或區塊。 SWIFT 中的交換，例如[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]定義為 SWIFT 標頭部分的串連 （SWIFT 區塊 1、 2、 3），後面接著一個 SWIFT 主體組件 （SWIFT 區塊 4），後面接著 SWIFT 結尾部分 （SWIFT 區塊 5）。  
  
## <a name="m"></a>M  
 **對應**  
 在一規格中的記錄和欄位以及其他規格中的記錄和欄位之間，定義對應關係的 XML 檔案。 對應包含 Extensible Stylesheet Language (XSL) 樣式表，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]用以執行該對應中描述的轉換。 您在 BizTalk 對應工具建立對應。  
  
 **訊息類型**  
 SWIFT 的標準版本指南，例如 「 接收針對出納 」 中定義的訊息格式的其中一個。 以"MT"後面接著三位數代碼通常代表訊息類型。  
  
## <a name="p"></a>P  
 **付款交易識別項 (PTI)**  
 提供起始客戶會附加至源自銀行，例如付款初始訊息和信用額度 Advices 付款相關銀行訊息的唯一交易識別碼。  
  
 **原則**  
 各種版本的商務規則集合。  
  
 **PTI**  
 付款交易識別碼。  
  
## <a name="r"></a>R  
 **規則**  
 條件和動作的配對。  
  
 **規則集**  
 相似規則的邏輯群組。 可做為規則引擎的群組/分割機制。  
  
## <a name="s"></a>S  
 **結構描述**  
 XML 檔案結構的定義。 因為它與相關的記錄和欄位在結構中的，結構描述會包含屬性資訊。  
  
 **全球 Interbank 財務 Telecommunication (SWIFT) 的協會**  
 針對全球 Interbank 財務電信協會。 提供傳訊服務銀行、 broker 經銷商、 投資管理員和市場付款、 庫房、 安全性和交易中的基礎結構的組織。 SWIFT 建立共用的全球資料處理和通訊連結的通用語言的國際財務交易。  
  
 **規格**  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 特有的 XML 結構描述。 規格會建立在 [BizTalk 編輯器] 中，而且可以根據業界標準 （例如快速、 EDIFACT、 x12 和 XML） 或一般檔案 （分隔、 位置或分隔和位置）。 BizTalk 對應工具會使用規格建立對應，這些規格和來源規格以及目的規格一樣都屬於開放式。  
  
 **強式名稱**  
 組成組件的識別名稱-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供），再加上由公開金鑰和組件產生的數位簽章。 因為組件資訊清單包含構成組件實作的所有檔案的檔案雜湊，便可透過只包含組件資訊清單的組件中的一個檔案產生的數位簽章。 具有相同的強式名稱組件都必須相同。  
  
 **直通式處理 (STP)**  
 透過多個步驟，需要手動介入的情況下訊息自動處理。 通常用於從接收的訊息來自 SWIFT 的金融機構在結果中之交易的金融機構中; 內部系統張貼處理路徑或從外部指示或動作的結果訊息，透過 SWIFT 或其他財務的基礎結構; 已傳輸的金融機構的接收或者，從內部的金融機構系統傳輸的一或多個相關訊息透過 SWIFT 或其他財務基礎結構。  
  
 **SWIFT 標準發行指南 (SRG)**  
 提供的 FIN 訊息集更新與建議標準 SWIFT 發行集。 這是多磁碟區組文件定義的配置和欄位每個訊息類型、 有效的值和格式的每個欄位、 網路規則套用到每則訊息，以及任何使用規則和常見的作法。 來自 SWIFT 的訂用帳戶服務使用此 CD 發行集。  
  
 **系統會產生訊息結尾 (SYS)**  
 附加至訊息的 SWIFT 網路結尾傳遞到金融機構，指出 FIN 服務產生的訊息。 範例包括廣播，回應使用者要求和報表。  
  
## <a name="u"></a>U  
 **唯一匯款識別元 (URI)**  
 商務交換的交換參與同步處理銀行 RosettaNet 付款里程碑程式所產生的識別項。  
  
## <a name="x"></a>X  
  
 **Xml-data Reduced (XDR)**  
 早期的語言，用來建立識別的結構與特定的 XML 文件條件約束的結構描述。 XML 資料精簡指的是已在提供的 XML 資料結構描述規格的子集[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]XML Parser (MSXML) 3.0 和更新版本。 它會執行相同的基本工作和 DTD，但更強大且彈性。 DTD 不同，這需要它自己的語言與語法，XDR 使用 XML 語法對本身的語言。 與 XSD，只有最近所推薦的標準，不同的是 XDR 已實作，而且可由[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]設法 W3C XML 結構描述工作群組所建議的標準 XSD 的存在。  
  
 **XML 結構描述定義 (XSD)**  
 W3C XML 結構描述工作小組所提議用於定義結構描述的語言。 結構描述可用於強制執行結構及/或條件約束可以有效地使用其他 XML 文件內的資料類型的項目。 可用來撰寫 XML 結構描述的完整指定和目前建議標準 XML 結構描述定義參考。 只有已發佈的版本，您可以使用 XSD 規格最近才完成，因為支援[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]XML Core Services (MSXML) 4.0。 它會執行相同的基本工作和 DTD，但更強大且彈性。 DTD 不同，這需要它自己的語言與語法，XSD 使用 XML 語法對本身的語言。 XSD 密切類似，並擴充 XDR 的功能。 W3C 建議使用 XSD 做為標準定義 XML 結構描述。
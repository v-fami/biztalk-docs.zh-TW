---
title: SWIFT 加速器，BizTalk Server 中的詞彙 |Microsoft Docs
description: 一般詞彙和定義了解，並了解如何使用 BizTalk Accelerator for SWIFT
ms.custom: ''
ms.date: 08/16/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7331beb-f6a7-4eea-8b31-28f5d15666d0
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6ab7cefe79d59927b481bf20d8b0961bf296595
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009471"
---
# <a name="glossary"></a>詞彙
下列詞彙和定義，則會使用 Microsoft BizTalk Accelerator for SWIFT。  
  
## <a name="a"></a>只有在次要複本設定成手動容錯移轉模式，而且至少一個次要複本目前與主要複本 SYNCHRONIZED 時，  
 **組譯工具**  
 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 「 組合 」 階段的輸出管線處理期間叫用的傳送管線元件。 組譯工具通常會序列化成一些一般檔案格式從 XML 輸出訊息的作業。  
  
 **組件**  
 主要建置組塊的 Microsoft[!INCLUDE[btsDotNetFramework](../../includes/btsdotnetframework-md.md)]應用程式。 它是重複使用、 版本控制、 安全性和部署的基本單位。 它是顯示程式設計人員必須是單一動態連結程式庫 (DLL) 或可執行檔 (EXE) 的檔案集合。  
  
 **組件快取**  
 並排顯示的組件的儲存體使用全機器程式碼快取。 有兩個部分快取。 全域組件快取包含明確安裝在電腦上的許多應用程式之間共用的組件。 下載快取會儲存從網際網路下載的程式碼或內部網路網站，與觸發下載，以便代表一個應用程式下載程式碼的應用程式隔離，或頁面不會影響其他應用程式。  
  
## <a name="b"></a>B  
 **銀行識別代碼 (BIC)**  
 SWIFT 所定義，用來識別金融機構中，程式碼。  
  
 **商務規則編輯器 」 工具**  
 用來編寫原則的圖形使用者介面工具。  
  
 **商務規則引擎 (BRE)**  
 根據事實評估規則，並依照其評估結果啟始動作的執行階段推斷引擎。  
  
## <a name="c"></a>c  
 **條件式規則**  
 規則，指定 SWIFT 訊息類型的欄位間的關聯性。 SWIFT 標準版本指南中定義條件式規則。  
  
## <a name="d"></a>D  
 **解譯器**  
 A[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]接收輸入的管線處理的解譯階段期間叫用的管線元件。 解譯器 」 通常會剖析成 XML 的輸入的訊息從某些一般檔案格式的作業。  
  
## <a name="e"></a>E  
 **錯誤碼**  
 程式碼，其中包含字母，後面接著兩個數字，指出特定的指定的訊息類型的規則違規情形。  
  
 **可延伸標記語言 (XML)**  
 由全球資訊網協會 (W3C) 所開發的規格，讓程式設計人員能建立超越標準 HTML 功能的自訂標籤。 而 HTML 則使用預先定義的標記來描述頁面中的項目，則 XML 會讓頁面的開發人員所定義的標記。 對於任何虛擬的資料項目 (例如產品或到期金額)，標籤都可以針對特定的應用程式來使用。 這讓網頁也可以具有和資料庫記錄相同的功能。  
  
 **可延伸樣式表語言 (XSL)**  
 樣式表的可延伸標記語言 (XML) 文件格式。 XSL 用來在相同的方式，該階層式樣式表 (CSS) 用來定義顯示的超文字標記語言 (HTML) 中定義的 XML 顯示。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 會使用 XSL 當做翻譯語言兩種規格之間。  
  
## <a name="f"></a>F  
 **FIN**  
 財務 SWIFT 已定義的結構描述和驗證標準 SWIFT 標準發行指南 2003年中的訊息。  
  
## <a name="g"></a>G  
 **全域組件快取 (GAC)**  
 整個電腦的程式碼快取，它會存放供電腦上多個應用程式共用而特別安裝的組件。 部署在全域組件快取中的應用程式必須具有強式名稱。  
  
## <a name="h"></a>H  
 **使用安全超文字傳輸通訊協定 (HTTPS)**  
 超文字傳輸通訊協定 (HTTP) 使用 Secure Sockets Layer (SSL) 加密通訊協定。  
  
## <a name="i"></a>I  
 **交換**  
 完整的訊息，用來組成較小的訊息部分或區塊。 SWIFT 中的交換，例如[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]定義為 SWIFT 標頭部分的串連 （SWIFT 區塊 1、 2、 3），後面接著的 SWIFT 的內文部分 （SWIFT 區塊 4），後面接著 SWIFT 結尾部分 （SWIFT 封鎖 5）。  
  
## <a name="m"></a>M  
 **對應**  
 在一規格中的記錄和欄位以及其他規格中的記錄和欄位之間，定義對應關係的 XML 檔案。 對應包含 Extensible Stylesheet Language (XSL) 樣式表，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]用以執行在對應中描述的轉換。 您在 BizTalk 對應工具建立對應。  
  
 **訊息類型**  
 其中一個 SWIFT 的標準發行指南，例如 「 接收針對付款 」 中定義的訊息格式。 訊息類型通常會以 「 MT"後面接著三位數代碼。  
  
## <a name="p"></a>P  
 **付款交易識別碼 (PTI)**  
 提供初始的客戶會附加至付款相關的銀行訊息來自 banks，例如付款初始訊息和信用額度建議唯一交易識別碼。  
  
 **原則**  
 各種版本的商務規則集合。  
  
 **PTI**  
 付款交易識別碼。  
  
## <a name="r"></a>R  
 **rule**  
 條件和動作的配對。  
  
 **規則集**  
 相似規則的邏輯群組。 可做為規則引擎的群組/分割機制。  
  
## <a name="s"></a>S  
 **schema**  
 XML 檔案結構的定義。 結構描述會包含屬性資訊，因為它適用於記錄和在結構內的欄位。  
  
 **全球 Interbank 財務電信 (SWIFT) 的協會**  
 針對全球 Interbank 財務電信協會。 提供傳訊服務，銀行、 訊息代理程式經銷商、 投資經理和市場中付款、 財務、 安全性和商業的基礎結構的組織。 SWIFT 建立共用的全球資料處理和通訊連結的通用語言的國際的財務交易。  
  
 **規格**  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 特有的 XML 結構描述。 規格會建立在 「 BizTalk 編輯器 」 中，而且可以根據業界標準 （例如 SWIFT，EDIFACT，x12 和 XML) 或一般檔案 （分隔符號、 位置，或是分隔和位置）。 BizTalk 對應工具會使用規格建立對應，這些規格和來源規格以及目的規格一樣都屬於開放式。  
  
 **強式名稱**  
 包含的組件的身分識別的名稱-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供） — 再加上由公開金鑰和數位簽章產生組件。 因為組件資訊清單包含構成組件實作的所有檔案的檔案雜湊，它便可透過只包含組件資訊清單的組件中的一個檔案產生數位簽章。 具有相同的強式名稱組件都必須相同。  
  
 **直通式處理 (spanning tree Protocol)**  
 透過多個步驟，需要手動介入的情況下訊息自動處理。 通常被套用至的處理路徑中接收訊息來自 SWIFT 在金融機構的財務機構; 內部系統中產生交易張貼或從接收外部的指示或在透過 SWIFT 或其他財務的基礎結構; 的結果訊息傳輸的財務機構的動作或者，您也可以從內部的財務機構系統傳輸的一或多個相關訊息透過 SWIFT 或其他財務的基礎結構。  
  
 **SWIFT 標準版指南 (SRG)**  
 FIN 訊息集合提供的更新及建議的標準 SWIFT 發行集。 這是多重磁碟區組定義的配置和欄位的每個訊息類型、 有效的值，和每個欄位、 網路規則套用到每則訊息，以及任何使用規則或常見做法的格式的文件。 來自 SWIFT 的訂用帳戶服務使用此 CD 發行集。  
  
 **系統產生的訊息結尾 (SYS)**  
 附加至訊息的 SWIFT 網路結尾傳遞到金融機構，指出 FIN 服務產生的訊息。 範例包括廣播，回應使用者要求和報告。  
  
## <a name="u"></a>u  
 **唯一匯款識別元 (URI)**  
 商務交換的交換參與 RosettaNet 付款里程碑計劃，以同步處理銀行所產生的識別項。  
  
## <a name="x"></a>X  
  
 **Xml-data Reduced (XDR)**  
 最早的語言，用來建立結構描述，用來識別的結構和特定的 XML 文件條件約束。 XML 資料精簡指的是已使用 Microsoft XML Parser (MSXML) 3.0 在和更新版本的 XML 資料結構描述規格的子集。 它會執行相同的基本作業，做為 DTD 中，但更強大且彈性。 DTD 不同，這需要它自己的語言與語法，XDR 使用 XML 語法對本身的語言。 不同於 XSD 最近才被建議為標準，XDR 實作，並由 Microsoft 所提供以及大眾 XSD 被 W3C XML 結構描述工作團隊為。  
  
 **XML 結構描述定義 (XSD)**  
 一種語言，用於定義結構描述的 W3C XML 結構描述工作團隊建議。 結構描述可用於強制執行結構及/或限制可以有效地使用其他 XML 文件內的資料類型的項目。 XML 結構描述定義是指在撰寫 XML 結構描述中使用的完整指定且目前被建議標準。 因為只有已發行的 Microsoft XML Core Services (MSXML) 4.0 提供的 XSD 規格會是唯一最近定案，支援。 它會執行相同的基本作業，做為 DTD 中，但更強大且彈性。 不同於 DTD 中，這需要它自己的語言與語法，XSD 會對本身的語言使用 XML 語法。 XSD 密切類似，並擴充 XDR 的功能。 W3C 目前已建議使用 XSD 做標準來定義 XML 結構描述。
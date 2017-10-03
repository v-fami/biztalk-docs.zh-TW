---
title: "使用 BRE 原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE policies, about BRE policies
- BRE policies
ms.assetid: 4470f2b3-6891-46d7-9ba1-848f90d0767d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624af2a9c05e1a419acac66eeb6a1aea8d29d695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-bre-policies"></a>使用 BRE 原則
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]驗證 SWIFT 訊息所使用商務規則引擎 (BRE) 原則中所述*SWIFT 參考指南*。 這些原則包括下列各項：  
  
-   格式化  
  
-   數值範圍  
  
-   有效的清單項目  
  
-   網路規則與對應的錯誤代碼  
  
-   使用規則可從訊息內容驗證  
  
 這些原則不會包含不是依存於訊息內容或任何跨訊息驗證的一般作法。  
  
 基本欄位選用性和基數，實作格式化參考 SWIFT 基底 Types.xsd 結構描述的訊息結構描述時，會實作訊息 （和標頭和結尾） 的 XSD 結構描述。 每個訊息類型的兩個特定的原則定義與每個訊息相關聯的規則：  
  
-   主機原則 (MT*xxx*_Master_Policy.xml)  
  
-   驗證原則 (MT*xxx*_Validation_Policy.xml)  
  
 每個訊息類型的主要原則會叫用套用至該訊息類型的特定原則。 這些特定的原則包含特殊欄位會檢查該一般函式實作、 網路規則和使用規則。 訊息的主要原則是第一個原則，該訊息執行。 原則的清單包含訊息類型的驗證原則。 每個主要原則已建構 [如果這個訊息類型，然後執行原則的清單]。  
  
 每個訊息類型的驗證原則會列出其他外部的規則實作，例如欄位碼的單一欄位檢查，或使用欄位的特定詞彙。 這些個別規則通通常在兩個或多個訊息，因為它們是特定的欄位。 沒有程式碼，BRE 詞彙，A4SWIFT_Codelists 提供允許的欄位值。  
  
 *SWIFT 參考指南*分別實作每個網路規則。 每個網路規則說明組訊息類型*SWIFT 參考指南*定義。  
  
 A4SWIFT 安裝 A4SWIFT 安裝時，不會安裝規則。 您選取的結構描述，並建置並部署組件之後，您可以使用 BRE 部署公用程式來選取和部署的結構描述設定適當的規則。 若要部署選取之訊息的規則，執行此公用程式並選取相關的組件。 此工具會選取對應的主要原則、 驗證原則和任何參考的網路或其他規則。  
  
 A4SWIFT 關聯 A4SWIFT 規則的兩種類型的詞彙。 第一個詞彙是 A4SWIFT_Codelist，其中包含各種不同的程式碼清單值。 第二個詞彙是 A4SWIFT_Functions。 這些詞彙是[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]邏輯驗證和計算的類別。  
  
 您可以將 BRE 驗證組態參數設定為 true，以叫用 A4SWIFT 解譯器在接收管線中，規則。 您也可以叫用從協調流程的規則。 您無法叫用由 A4SWIFT 組譯工具 (ASM) 的規則。 您必須使用協調流程或接收管線，來驗證針對結構描述的執行個體，並叫用規則。  
  
 如果訊息無法結構描述驗證或商務規則，A4SWIFT 會準備包含描述發現之錯誤的錯誤集合和表示錯誤中的欄位或訊息中發生錯誤的位置。 如需詳細資訊，請參閱[處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。  
  
 您可以加入其他規則 A4SWIFT 提供的集合。 比方說，如果您採用市場作法群組規則，會影響一組新的訊息時，您可以實作包含一或多個新的驗證，視需要的主要原則的新版本。 同樣地，如果您強制執行額外的單一欄位檢查，您可以將這些檢查加入訊息驗證原則的新版本。 您可以實作新的驗證為新的規則或詞彙函式。  
  
 此部分包含：  
  
-   [啟用驗證的銀行識別項代碼](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)  
  
-   [管理 Bicplus 資料表 A4SWIFT 資料庫中](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)  
  
-   [支援前置 0 量欄位驗證](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md)  
  
-   [設定位移量驗證](../../adapters-and-accelerators/accelerator-swift/setting-offsets-for-amount-validation.md)  
  
-   [移除的使用方式規則驗證](../../adapters-and-accelerators/accelerator-swift/removing-usage-rule-validation.md)
---
title: 使用 BRE 原則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BRE policies, about BRE policies
- BRE policies
ms.assetid: 4470f2b3-6891-46d7-9ba1-848f90d0767d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdb05d6f11d0d4d4f4ef5fd990d05c51b5e0df64
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968951"
---
# <a name="working-with-bre-policies"></a>使用 BRE 原則
Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]驗證 SWIFT 訊息所使用商務規則引擎 (BRE) 原則中所述*SWIFT 參考指南*。 這些原則包括：  

- 格式化  

- 數值範圍  

- 有效的清單項目  

- 使用對應的錯誤代碼的網路規則  

- 使用規則可從訊息內容驗證  

  這些原則不包含不依存於訊息內容或任何跨訊息驗證的一般作法。  

  基本欄位選用性和基數，實作格式化參考 SWIFT 基底 Types.xsd 結構描述的訊息結構描述時，會實作訊息 （和標頭和結尾） 的 XSD 結構描述。 每種訊息類型的兩個特定原則會定義每個訊息相關聯的規則：  

- 主要原則 (MT*xxx*_Master_Policy.xml)  

- 驗證原則 (MT*xxx*_Validation_Policy.xml)  

  每個訊息類型的主要原則會叫用特定的原則套用至該訊息類型。 這些特定的原則包括特殊欄位可讓您檢查該一般函式實作、 網路規則，以及使用規則。 訊息的主要原則是針對該訊息執行的第一個原則。 原則清單會包含訊息類型的驗證原則。 每個主要原則已建構 [如果這個訊息類型，然後執行的原則清單]。  

  每個訊息類型的驗證原則會列出其他外部的規則實作，例如欄位碼的單一欄位檢查，或欄位會使用特定的詞彙。 這些個別的規則會在兩個或多個訊息，通常通用的因為它們是欄位特有。 BRE 詞彙，A4SWIFT_Codelists 不程式設計的程式碼，提供允許的欄位值。  

  *SWIFT 參考指南*獨立實作每一個網路規則。 每個網路規則解決一組訊息型別*SWIFT 參考指南*定義。  

  A4SWIFT 安裝 A4SWIFT 安裝時，不會安裝規則。 您要選取的結構描述，以及建置和部署組件之後，您可以使用 BRE 部署公用程式來選取和部署結構描述集合的適當規則。 若要部署選取之訊息的規則，執行此公用程式並選取相關的組件。 此工具會選取對應的主要原則、 驗證原則和任何參考的網路或其他規則。  

  A4SWIFT 關聯 A4SWIFT 規則的兩種類型的詞彙。 第一個詞彙是 A4SWIFT_Codelist，其中包含各種不同的程式碼清單值。 第二個詞彙是 A4SWIFT_Functions。 這些詞彙是[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]邏輯驗證和計算的類別。  

  您可以將 BRE 驗證組態參數設定為 true，以叫用 A4SWIFT 解譯器在接收管線中，規則。 您也可以叫用協調流程中的規則。 您無法叫用由 A4SWIFT 組譯工具 (ASM) 的規則。 您必須使用協調流程或接收管線，以驗證對結構描述執行個體，並叫用的規則。  

  如果訊息無法結構描述驗證或商務規則，A4SWIFT 會準備包含描述發現之錯誤的錯誤集合和表示錯誤中的欄位或訊息中發生錯誤的位置。 如需詳細資訊，請參閱 <<c0> [ 處理失敗的訊息訂閱](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md)。  

  您可以新增額外的規則，A4SWIFT 提供的集合。 比方說，如果您採用的市場做法規則會影響一組新的訊息時，您可以實作包含一或多個新驗證，請視需要的主要原則的新版本。 同樣地，如果您加諸額外的單一欄位檢查，您可以加入這些檢查訊息驗證原則的新版本。 您可以實作新的驗證與新的規則，或做為詞彙。  

  此部分包含：  

- [啟用驗證 Bank Identifier Code](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md)  

- [管理 A4SWIFT 資料庫中的 Bicplus 資料表](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md)  

- [金額欄位驗證中支援前置零](../../adapters-and-accelerators/accelerator-swift/supporting-leading-zeros-in-amount-field-validations.md)  

- [設定金額驗證的位移](../../adapters-and-accelerators/accelerator-swift/setting-offsets-for-amount-validation.md)  

- [移除使用方式規則驗證](../../adapters-and-accelerators/accelerator-swift/removing-usage-rule-validation.md)

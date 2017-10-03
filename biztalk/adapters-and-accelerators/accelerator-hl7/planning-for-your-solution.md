---
title: "規劃您的解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Greenfield project
- security, BTAHL7
- BTAHL7, security
- installing, planning
- installing, installation types
- HL7, security
- security, HL7
- Embedded installation
- Migration project
- Coexistence installation
ms.assetid: a108c6d0-dd51-4bf9-85a0-103f60fae971
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73b39dc63621583fc0ecc495d99e9307a2308db6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-your-solution"></a>規劃您的方案
本節提供有關計劃時應該考慮的事項的資訊您[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]方案。  
  
 您可以下列方式來實作 BTAHL7:  
  
-   **綠地專案**。 此案例中是新的 BTAHL7 安裝。  
  
-   **移轉專案**。 健康照護組織之所以現有的 integration broker 時，就會發生此情況。 組織將移轉到 BTAHL7。  
  
-   **共存**。 此案例將會與另一個整合引擎 BTAHL7-並存安裝。  
  
-   **內嵌**。 此案例牽涉到整合 BTAHL7 內的特定業務應用程式。 您可以使用 BTAHL7 HL7 訊息功能新增至該應用程式。  
  
 人們傾向於低估的一段時間相較於在第一次建立它們的工作管理的應用程式所需的投入時間量。 尋找在大型的分散式的機構，需要執行一些複雜的資料處理和管理工作陣列時，這是特別有用。 醫院或整合式健全狀況傳遞組織的這類機構的絕佳範例。 這類機構面臨需要提供的軟體來支援各種函式，以啟用要傳遞至應用程式以避免重複和錯誤資料的項目，以提供使用者和維護程式的訓練需求的應用程式資訊軟體，並提供以取代過時或過期的應用程式的改進的。 這個替代程序有自己用於測試和教育的需求。  
  
 不可能 （極為耗費資源） 的這類機構管理所有其功能與單一整合應用程式。 在一開始，機構不打算要繫結其吧，單一廠商，並將找不到它們需要透過單一廠商的所有函式。 第二個就地機構處理簡單作業需求使得機構滿意單一整合式應用程式。 因此，機構將支援多個應用程式的需求。 為了讓這些應用程式交互操作，應用程式必須以交換資訊的介面。 應用程式和相關的介面數目通常是相當大。 指定此分散式應用程式架構，介面引擎是一段時間管理機構資料處理的用戶的金鑰。 重要的問題是移轉、 對應和教育。 BTAHL7 的工作就是解決這些問題，簡單而盡可能有效率：  
  
-   **對應**。 在介面實作的最大作業中，建立應用程式/資料庫結構與用在介面中的資料結構之間的對應。 此工具會將此簡單和自然的任何項目是理想的狀況。 此外，因為對應文件將成為介面和應用程式開發人員所使用的規格，請務必要能夠輕鬆地產生它的文件。 使用 BTAHL7 組態總管 中， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]工具來開發及實作這些對應。  
  
-   **移轉**。 當應用程式變更，您必須維護應用程式交互操作性經過一段時間。 如果您考慮到取代單一應用程式相關的問題，需要是更新的資料來源對應至適用的介面。 介面引擎有應該只是一種。 您應該考慮介面其中已安裝，而且如果介面標準會隨時間而改變。 您會發現，經過一段時間介面標準變更且必須進行移轉的常見標準。 建議的移轉計劃考量未來的介面中的任何變更。 您需要將之間的標準，以及標準的不同版本之間的對應。 此外，單一標準範圍內 — 尤其是彈性一個例如 HL7 V2 — 您需要使用 （跨越許多應用程式） 多個相同的標準實作的處理。 介面引擎處理的方式在這種複雜性很容易管理。  
  
     金鑰的移轉工作就是從一個標準的介面主體移轉至另一個。 以下是移轉所有使用舊的版本新的對應工作 — 佔據帳戶介面特定當地語系化和擴充功能，它可以是複雜的程序。 此工具應該提供這項移轉的協助。  
  
     您可以使用 [BTAHL7 組態總管驗證] 索引標籤來指定任何額外的訊息類型結構描述的命名空間。  
  
-   **教育**。 管理與支援的應用程式的人員會隨時間變更。 此外，由於之集合的應用程式的互通性功能的核心介面，他們的文件將會由提供金鑰管理整個企業中的工具。 基於上述這兩個原因，是重要提供易於使用，並且容易維護文件） 的介面規格、 b） 的應用程式和 introversion 對應，以及自訂及當地語系化活動 c） 的基本原理。  
  
## <a name="see-also"></a>另請參閱  
[了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)
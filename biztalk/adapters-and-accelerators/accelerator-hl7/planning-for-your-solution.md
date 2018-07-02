---
title: 規劃您的解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20e41137d8e300453d3dc4eba7fee6e9dd6ecc0b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977271"
---
# <a name="planning-for-your-solution"></a>規劃您的解決方案
本節提供的資訊規劃您的 Microsoft 時應該考慮的事項[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]解決方案。  
  
 您可以透過下列方式來實作 BTAHL7:  
  
- **Greenfield 專案**。 此案例中是新的 BTAHL7 安裝。  
  
- **移轉專案**。 健康醫療組織淘汰現有的 integration broker 時，就會發生這種情況。 組織將移轉至 BTAHL7。  
  
- **共存**。 此案例將會與另一個整合引擎 BTAHL7-並存安裝。  
  
- **內嵌**。 此案例牽涉到整合 BTAHL7 內的特定業務應用程式。 您可以使用 BTAHL7 將 HL7 傳訊功能新增至該應用程式。  
  
  人們傾向於低估的一段時間相較於當初建立它們所需的工作管理應用程式所需的投入量。 尋找在大型的分散式的機構都需要執行複雜的各種資料處理和管理工作時，這是特別有用。 醫院或整合的健康狀態傳遞組織的此類機構的絕佳範例。 這類的機構都面臨需要提供的軟體可支援大量的函式，以允許從應用程式，以避免重複和錯誤資料的項目，以供使用者和其困難之處的訓練需求的應用程式傳遞的資訊軟體，並提供取代過時或過期的應用程式藉由改善的。 這個替代程序都有自己用於測試和教育的需求。  
  
  它是不可能 （費不貲） 這類的機構，以管理所有其功能與單一整合的應用程式。 當初，機構不會想要將繫結其命運的單一廠商，並將不會發現他們需要透過單一廠商的所有函式。 在第二個位置，機構處理的簡單作業需求會使得機構滿足了單一的整合式應用程式。 因此，機構將支援多個應用程式及其需求。 為了讓這些應用程式交互操作，應用程式會需要交換資訊的介面。 應用程式和相關的介面的數目通常是相當大。 指定此分散式應用程式架構、 介面引擎是管理經過一段時間的資料處理機構金鑰檢測。 重要的問題是移轉、 對應及教育版。 BTAHL7 的工作是要解決這些問題，盡可能簡單，盡可能有效率：  
  
- **對應**。 介面實作中最大的工作建立應用程式/資料庫結構和介面中使用的資料結構之間的對應。 此工具會將此簡單且自然的任何項目是很好。 此外，對應文件將成為介面與應用程式的開發人員所使用的規格，因為務必要能夠輕鬆地產生它的 xml 文件。 您使用 BTAHL7 設定總管，Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]以及 BizTalk Server 工具進行開發及實作這些對應。  
  
- **移轉**。 隨著應用程式的變更，您必須維持一段時間的應用程式的互通性。 如果您考慮取代單一應用程式與相關的問題時，需要是更新資料來源對應到適當的介面。 使用介面引擎應該有其中一種。 您應該考慮其中已安裝介面，如果介面標準會隨時間而改變。 您會發現，經過一段時間介面標準變更且需要移轉的普遍的標準。 建議的移轉計劃考量未來介面的任何變更。 您需要將對應標準，以及不同版本的標準。 此外，以單一標準範圍內 — 尤其是彈性一個例如 HL7 V2 — 您必須處理 （跨許多應用程式） 的相同標準的多個實作。 介面引擎處理這種複雜性的方式，就可以輕鬆地管理。  
  
   金鑰的移轉工作是從一個標準的介面主體移轉至另一個。 這裡的工作是移轉所有使用舊的版本到新的對應，花在帳戶介面特定當地語系化和延伸模組，它可以是複雜的程序。 此工具應該提供這項移轉的協助。  
  
   您可以使用 [BTAHL7 設定總管驗證] 索引標籤來指定任何額外的訊息類型結構描述的命名空間。  
  
- **教育**。 管理與支援的應用程式的相關人員會隨著時間改變。 此外，由於介面之集合的應用程式的互通性功能的核心，其文件會來自金鑰管理整個企業的工具。 基於這兩個上述原因，是非常有用的提供容易使用，且容易維護文件） 的介面規格、 b） 的應用程式和 introversion 的對應，以及 c） 是合乎常理的自訂與當地語系化的活動。  
  
## <a name="see-also"></a>另請參閱  
[了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)
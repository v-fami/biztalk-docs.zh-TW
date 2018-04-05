---
title: 開始使用 BizTalk Accelerator for HL7 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.gettingstarted
helpviewer_keywords:
- BizTalk Accelerator for HL7
- BizTalk Accelerator for HL7, getting started
- getting started
ms.assetid: e842d501-2037-4fd6-a518-d29b25877250
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bebe61b152c7a74c2d45c0604e23b0a39bc6a4fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="get-started-with-the-biztalk-accelerator-for-hl7"></a>開始使用 BizTalk Accelerator for HL7
使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)]，您可以開發醫療保健電腦系統之間的商務程序。 使用[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，開發人員、 IT 專業人員和介面分析師可在環境中工作一般跨醫療保健應用程式開發端對端整合 BTAHL7 為基礎的解決方案。  
  
 更具體來說，與[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]您可以：  
  
-   **簡化醫療保健應用程式整合**。 建置、 管理及追蹤分散式的商務程序使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]開發環境。  
  
-   **標準化醫療應用程式之間的臨床資料交換**。 轉換現有的資料傳輸至應用程式之間[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]標準。  
  
-   **提高效率**。 所有具有最少手動介入的醫療應用程式之間的通訊程序自動化。  

本節提供有關您可以使用的角色特定資訊[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]以便醫院和自動化企業對企業保健解決方案醫療保健舞內的企業應用程式整合 (EAI).  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]教學課程格式的四個個別案例提供每種方案類型。 在開始這些教學課程之前，您應該了解中的基本概念[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]、 工具和程序所需開始建置解決方案[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]。  

> [!TIP] 
> 您開始進行這些課程中前,[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。  
  
 以下描述提供每個有基本認識[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]教學課程。  
  
## <a name="end-to-end-tutorial"></a>端對端教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]端對端教學課程為您提供的詳細步驟可協助在 「 訂閱者 」 和 「 發行者 」 案例的商務程序。 此案例中是以 「 發行者 」，例如許可放電和傳輸系統會傳送訊息至特定訂閱者的情況。  
  
 訊息會路由傳送至[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]介面引擎，依序接收到處理程序，驗證、 重新格式化，並接著會將訊息路由至訂閱者。 在此案例中的 「 訂閱者 」 是醫院資訊和藥局系統。  
  
 此案例使用檔案和最小的較低層通訊協定 (MLLP) 配接器類型。 不需要注意的訂閱者 」，「 發行者 」 和[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]介面引擎將適當的通知傳送到 「 發行者 」 在處理訊息之後。  
  
## <a name="interrogative-tutorial"></a>Interrogative 教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interrogative 教學課程為您提供詳細的步驟來實作組織內的子系統之間的查詢回應系統。 在此案例中，在許可的特定業務 (LOB) 應用程式放電，和傳輸系統會將查詢傳送至醫院資訊系統取得病患實驗室結果。 醫院資訊系統收到查詢之後，它會傳送回系統發出查詢要求的資料。  
  
 此案例會使用 MLLP 做為傳輸通訊協定的所有訊息，包含通知。  
  
## <a name="message-enrichment-tutorial"></a>訊息豐富 」 教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]擴充教學課程為您提供詳細的步驟來解決特定商務問題： 訊息豐富 」 案例。 訊息豐富 」 案例是您不必加入或擴充的情況下，不是 HL7 相容及/或不完整的訊息。 這種情況可能會發生應用程式，例如病患註冊應用程式，或是會填入來自 XML 資料的訊息[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。  
  
 在訊息豐富 」 案例中，您可以擷取與訊息[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，並提供任何遺失的資料，例如，從病患記錄資料庫。 然後將訊息轉換，並將它傳送至實驗室、 保險或使用 MLLP 配接器任何舊版的特定業務 (LOB) 應用程式。  
  
## <a name="batching-tutorial"></a>批次的教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]批次處理教學課程為您提供的詳細步驟可接收和傳送批次的訊息。 批次當做單一複合訊息包含接收和/或傳送的一組個別訊息 （或通知）。  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]支援下列三個訊息批次處理案例：  
  
-   **分散的傳入批次**。 在此案例中，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收 HL7 訊息批次，並再將個別的訊息路由至目的地系統。  
  
-   **在批次 / 批次出**。[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收 HL7 訊息批次、 驗證，表示批次內的個別訊息並再將批次訊息路由至目的地系統。  
  
-   **建立批次 （或輸出批次處理）**。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收個別的訊息，批次處理它們之前進行路由至目的地系統。  
  
## <a name="tutorial-links"></a>教學課程的連結  
  
-   [端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)  
  
-   [Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)  
  
-   [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)  
  
-   [批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)
  
## <a name="see-also"></a>另請參閱
  
[殘障人士的協助工具](../../adapters-and-accelerators/accelerator-hl7/accessibility-for-people-with-disabilities5.md)
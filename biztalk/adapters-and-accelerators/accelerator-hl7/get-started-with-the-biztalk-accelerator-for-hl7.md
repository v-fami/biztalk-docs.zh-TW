---
title: 開始使用 BizTalk Accelerator for HL7 |Microsoft Docs
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
ms.openlocfilehash: 14559d888bc020a5772fbbc6eddf3ba4fdb4beb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989599"
---
# <a name="get-started-with-the-biztalk-accelerator-for-hl7"></a>開始使用 BizTalk Accelerator for HL7
使用 Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)]，您可以開發醫療保健電腦系統之間的商務程序。 使用[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，開發人員、 IT 專業人員和介面分析師可在通用的環境來開發跨醫療保健應用程式的端對端整合的 BTAHL7 架構解決方案。  
  
 更具體來說，與[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]您可以：  
  
- **簡化醫療保健應用程式整合**。 建置、 管理及追蹤分散式的商務程序使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]開發環境。  
  
- **標準化醫療應用程式之間的臨床資料交換**。 轉換現有的資料傳輸至應用程式之間[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]標準。  
  
- **提高效率**。 使用最少的手動介入的醫療應用程式之間的所有通訊程序都自動化。  

本節提供有關您可以使用的角色專屬資訊[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]以便在醫院和醫護競技場，自動化企業對企業的醫療保健解決方案的企業應用程式整合 (EAI).  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 提供每種方案中的四個不同的案例教學課程的格式。 這些教學課程之前，您應該了解中的基本概念[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]，以及工具和程序，才能開始建置解決方案[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]。  

> [!TIP] 
> 這些課程中，開始之前[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。  
  
 以下描述提供大致的了解每個[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]教學課程。  
  
## <a name="end-to-end-tutorial"></a>端對端教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]端對端教學課程會將您提供詳細的步驟，以便在 「 訂閱者 」 和 「 發行者 」 的案例中的商務程序。 此案例中是以 「 發行者 」，例如許可出院和傳輸系統會傳送訊息至特定的訂閱者的情況。  
  
 訊息將路由傳送至[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]介面引擎，進而接收程序，驗證、 重新格式化，並接著會將訊息路由至訂閱者。 在此案例中的 「 訂閱者 」 是醫院資訊系統和 Pharmacy 系統。  
  
 此案例使用檔案和最小的較低層通訊協定 (MLLP) 配接器類型。 不需要留意的 「 訂閱者 」，「 發行者 」 和[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]介面引擎處理訊息之後將適當的通知傳送到 「 發行者 」。  
  
## <a name="interrogative-tutorial"></a>詢問式教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]詢問式教學課程為您提供詳細的步驟來實作組織內的子系統之間的查詢回應系統。 在此案例中，的營運 (LOB) 應用程式中的許可，出院，，和傳輸系統會將查詢傳送至醫院資訊系統，以取得病患的實驗室結果。 醫院資訊系統收到查詢之後，它會傳送回系統發出查詢要求的資料。  
  
 此案例會使用 MLLP 做為傳輸通訊協定的所有訊息，包括通知。  
  
## <a name="message-enrichment-tutorial"></a>訊息擴充教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]擴充教學課程會將您提供詳細的步驟來解決特定商務問題： 訊息豐富 」 案例。 訊息豐富 」 案例是您不必加入或擴充的情況下，不符合規範 HL7 和/或不完整的訊息。 應用程式，例如病患註冊應用程式，或會填入來自 XML 資料的訊息可能會發生這種情況下[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。  
  
 您可以在訊息豐富 」 案例中，擷取的訊息[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，並提供任何遺漏的資料，例如從病患記錄資料庫。 然後將訊息轉換，並將它傳送至一個實驗室、 保險或使用 MLLP 配接器任何舊版的特定業務 (LOB) 應用程式。  
  
## <a name="batching-tutorial"></a>批次處理教學課程  
 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]批次處理教學課程會將您提供詳細的步驟，以接收和傳送批次的訊息。 批次處理為單一複合訊息包含接收和/或傳送一組個別的訊息 （或通知）。  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 支援下列三個訊息批次處理案例：  
  
- **片段化的輸入批次**。 在此案例中，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收 HL7 訊息批次中，並再將個別的訊息路由至目的系統。  
  
- **在批次 / 批次出**。[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收 HL7 訊息批次驗證個別訊息的批次內，然後將批次訊息路由傳送至目的地系統。  
  
- **建立批次 （或輸出批次處理）**。 [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 接收個別的訊息，批次處理它們之前先路由傳送至目的地系統。  
  
## <a name="tutorial-links"></a>教學課程的連結  
  
-   [端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)  
  
-   [詢問式教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)  
  
-   [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)  
  
-   [批次處理教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)
  
## <a name="see-also"></a>另請參閱
  
[行動不便人士的協助工具](../../adapters-and-accelerators/accelerator-hl7/accessibility-for-people-with-disabilities5.md)
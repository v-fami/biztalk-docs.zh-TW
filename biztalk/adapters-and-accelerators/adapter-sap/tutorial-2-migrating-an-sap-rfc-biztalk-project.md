---
title: 教學課程 2： 移轉 SAP RFC BizTalk 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- migrating, BizTalk project from previous version of the SAP adapter
- migration
- migrating, SAP RFC BizTalk project
ms.assetid: b4943613-23d2-4869-b033-ec07daabfac5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf741fdbbf996fa54c227cc879c850304413d25f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978983"
---
# <a name="tutorial-2-migrating-an-sap-rfc-biztalk-project"></a>教學課程 2： 移轉 SAP RFC BizTalk 專案
不同於以 WCF 為基礎的 SAP 配接器隨附於 Microsoft BizTalk Server 舊版[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在許多方面，包括：  
  
- 建立 BizTalk 專案的設計階段經驗。  
  
- 中繼資料的擷取體驗。  
  
- 結構描述檔案名稱和命名空間。  
  
- 資料類型對應。  
  
- 可以使用配接器執行的作業。  
  
- 在 BizTalk Server 管理主控台中的實體連接埠組態。  
  
  中的主題會說明這些差異[移轉 BizTalk 專案建立使用上一個版本的 SAP 配接器](http://msdn.microsoft.com/library/a486bac9-8952-43fd-8099-413f1491de37)。  
  
  不過，您可以對使用舊版的配接器建立 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
  本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。  
  
> [!NOTE]
>  在本教學課程中，為了保持簡潔，舊版的 SAP 配接器會稱為 vPrev SAP 配接器。 同樣地，使用 vPrev SAP 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。  
  
## <a name="sample-used-for-the-tutorial"></a>用於本教學課程的範例  
 本教學課程是以示範如何將 SAP 系統中叫用 RFC vPrev BizTalk 專案的範例 (SAP_RFC_Migration) 為基礎。 提供了範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱 <<c0> [ 配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須具有 vPrev BizTalk 專案。 本教學課程包含叫用 SD_RFC_CUSTOMER_GET RFC BizTalk 專案。  
  
-   您必須執行才能叫用使用 vPrev SAP 配接器 SD_RFC_CUSTOMER_GET RFC 的要求訊息。 要求訊息必須符合 RFC 使用 vPrev SAP 配接器所產生的結構描述。 本教學課程中所提供的範例包含這個要求訊息。  
  
-   [建立強式名稱金鑰檔案，並了解工具](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案使用舊版配接器的建立  
 若要叫用 RFC vPrev BizTalk 專案的關鍵要素是：  
  
-   **BizTalk 協調流程**。 這是簡單的協調流程會挑選要求訊息的檔案位置，要使用 SAP 的 SAP 系統的要求訊息傳送-接收的傳送埠、 接收回應，並將它儲存到另一個檔案的位置。  
  
-   **您想要在 SAP 系統中叫用 RFC 的結構描述**。 本教學課程包含叫用 SD_RFC_CUSTOMER_GET RFC BizTalk 專案。 Rfc 所產生的結構描述是 SD_RFC_CUSTOMER_GET__x32003.xsd。 此結構描述是使用 vPrev SAP 配接器所產生的。  
  
-   **要求訊息**。 要叫用 SD_RFC_CUSTOMER_GET RFC 的要求訊息。 要求訊息的結構描述符合 SD_RFC_CUSTOMER_GET RFC 的結構描述，因為呈現 vPrev SAP 配接器。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>如何移轉 BizTalk 專案可讓您建立使用舊版的配接器  
 本移轉教學課程的目標是要讓您傳送要求訊息，這符合 vPrev SAP 配接器使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]的結構描述。  
  
 不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：  
  
- 產生中繼資料的使用以 WCF 為基礎的 SD_RFC_CUSTOMER_GET RFC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 將叫用 RFC 使用 vPrev SAP 配接器的要求訊息來叫用 RFC 使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]vPrev SAP 配接器的回應訊息。  
  
- 建立 WCF 自訂 SAP 傳送接收 BizTalk Server 管理主控台中的連接埠。  
  
- 設定 WCF 自訂連接埠，若要使用的要求和回應的對應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1：修改 vPrev BizTalk 專案以便叫用 RFC](../../adapters-and-accelerators/adapter-sap/step-1-modify-the-vprev-biztalk-project-for-invoking-an-rfc.md)  
  
-   [步驟 2：在 BizTalk Server 管理主控台設定協調流程](../../adapters-and-accelerators/adapter-sap/step-2-configure-the-orchestration-in-biztalk-server-administration-console1.md)  
  
-   [步驟 3：測試已移轉的應用程式](../../adapters-and-accelerators/adapter-sap/step-3-test-the-migrated-application6.md)  
  
## <a name="see-also"></a>另請參閱  
 [SAP 配接器教學課程](../../adapters-and-accelerators/adapter-sap/sap-adapter-tutorials.md)
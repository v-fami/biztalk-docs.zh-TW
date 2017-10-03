---
title: "步驟 1： 設定應用程式集區識別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, application pools
- application pools
ms.assetid: 66286327-8580-4378-89ee-ddd7204b03c6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e61ee2994e81c3fdd352506d6a9757cde557fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-application-pool-identity"></a>步驟 1： 設定應用程式集區識別
在本教學課程中，您可以使用應用程式集區中的[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]網際網路資訊服務 (IIS) 處理協調流程，您將發佈為 Web 服務。 應用程式集區是由背景工作處理序的一個或多個 url 群組。  
  
 應用程式集區的識別是應用程式集區的工作者處理序所執行的服務帳戶的名稱。 根據預設，應用程式集區是以 Network Service 使用者帳戶，具有低層級的使用者存取權限，並不足以進行本教學課程函式運作。 基於安全性理由，您想要設定應用程式集區識別的使用者帳戶，絕對最小權限，但在最低權限可以寫入組態資料庫 (也稱為 BizTalk 與 MessageBox 資料庫 (BizTalkMsgBoxDb)管理資料庫或 BizTalkMgmtDb）。  
  
### <a name="to-change-the-service-account-under-which-an-application-pool-runs"></a>若要變更應用程式集區所執行的服務帳戶  
  
1.  按一下**啟動**，指向 **程式**，指向 **系統管理工具**，然後按一下**網際網路資訊服務 (IIS) 管理員**.  
  
2.  在 [網際網路資訊服務 (IIS) 管理員] 中，展開本機電腦，及**應用程式集區**。  
  
3.  以滑鼠右鍵按一下您想要設定的應用程式集區 (依預設，此教學課程中，執行**DefaultAppPool**)，然後按一下 **屬性**。  
  
4.  在 [DefaultAppPool 屬性] 對話方塊上**識別**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**預先定義的**|取消選取**預先定義的**。 **預先定義的**指的是標準的服務帳戶，如下所示：<br /><br /> -   **網路服務**（預設值），其中包含可用於存取遠端電腦上的資源的低層級的使用者存取權限。<br />-   **本機服務**，具有低層級的存取權限。 您不需要在遠端電腦上的資源的存取權的情況下使用這項設定。<br />-   **本機系統**，這是具有多個與 Network Service 或 Local Service 帳戶的使用者權限的帳戶。|  
    |**可設定**|選取**可設定**。 **可設定**指的是已註冊的使用者名稱。|  
    |**使用者名稱**|輸入要在其下運作的工作者處理序的帳戶的使用者名稱。|  
    |**密碼**|輸入密碼。|  
  
5.  按一下 **[確定]**。  
  
    > [!NOTE]
    >  此外，為了提高安全性，您可以建立全新的應用程式集區的權限為本教學課程量身訂做的自訂身分識別下執行。  
  
 若要繼續[步驟 2： 建立新的專案](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
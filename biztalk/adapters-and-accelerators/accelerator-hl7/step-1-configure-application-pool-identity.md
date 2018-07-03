---
title: 步驟 1： 設定應用程式集區身分識別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message enrichment tutorial, application pools
- application pools
ms.assetid: 66286327-8580-4378-89ee-ddd7204b03c6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cdbc019b2e36ea8c50d97ff03597374cb07253
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988487"
---
# <a name="step-1-configure-application-pool-identity"></a>步驟 1： 設定應用程式集區識別
在本教學課程中，您可以使用 應用程式集區中 Microsoft Internet Information Services (IIS) 來處理協調流程，您將發佈為 Web 服務。 應用程式集區是由背景工作處理序的一或多個 Url 群組。  

 應用程式集區的識別是應用程式集區的工作者處理序所執行的服務帳戶的名稱。 根據預設，應用程式集區會在 Network Service 使用者帳戶，擁有低層級的使用者存取權限，並不足以執行本教學課程中函式下作業。 基於安全性理由，您想要設定給使用者帳戶的應用程式集區識別的絕對最低權限，但在寫入組態資料庫 (也稱為 BizTalk 與 MessageBox 資料庫 (BizTalkMsgBoxDb) 的最低權限管理資料庫或 BizTalkMgmtDb）。  

### <a name="to-change-the-service-account-under-which-an-application-pool-runs"></a>若要變更應用程式集區所執行的服務帳戶  

1. 按一下 **開始**，指向**程式**，指向**系統管理工具**，然後按一下  **Internet Information Services (IIS) Manager**.  

2. 在 [Internet Information Services (IIS) 管理員] 中，展開 [本機電腦]，然後展開**應用程式集區**。  

3. 以滑鼠右鍵按一下您想要設定應用程式集區 (根據預設，本教學課程中會執行**DefaultAppPool**)，然後按一下**屬性**。  

4. 在 [Defaultapppool] 對話方塊中，在**識別**索引標籤上，執行下列動作：  


   |     使用     |                                                                                                                                                                                                                                                                     以進行此動作                                                                                                                                                                                                                                                                      |
   |------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |  **預先定義的**  | 取消選取**預先定義的**。 **預先定義的**指的是標準的服務帳戶，如下所示：<br /><br /> -   **網路服務**（預設值），其中包含可用來在遠端電腦上的資源的存取權的低層級的使用者存取權限。<br />-   **本機服務**，其具有低層級的存取權限。 您不需要在遠端電腦上的資源的存取權的情況下使用此設定。<br />-   **本機系統**，這是具有多個與 Network Service 或 Local Service 帳戶的使用者權限的帳戶。 |
   | **可設定** |                                                                                                                                                                                                                                     選取 **可設定**。 **可設定**指的是已註冊的使用者名稱。                                                                                                                                                                                                                                      |
   |  **使用者名稱**   |                                                                                                                                                                                                                                輸入想要操作的工作者處理序帳戶的使用者名稱。                                                                                                                                                                                                                                |
   |   **密碼**   |                                                                                                                                                                                                                                                                 輸入密碼。                                                                                                                                                                                                                                                                  |


5. 按一下 [確定] 。  

   > [!NOTE]
   >  或者，為了提高安全性，您可以建立全新的應用程式集區會在您建立專供本教學課程中的權限的自訂身分識別下執行。  

   請繼續進行[步驟 2： 建立新的專案](../../adapters-and-accelerators/accelerator-hl7/step-2-create-a-new-project.md)。  

## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)
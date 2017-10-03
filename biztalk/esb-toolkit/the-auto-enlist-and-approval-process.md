---
title: "自動登記和核准程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfd3e72e-e28b-4ee3-bc4a-89ef3f64e6d5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333e1403ffd45f80a98d3eb17f5d3aa2b63c7798
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-auto-enlist-and-approval-process"></a>自動登記和核准程序
您可以設定 ESB 管理入口網站，若要發行 Microsoft BizTalk Server 端點有兩種：  
  
-   它可以透過其中系統管理員必須確認及核准註冊要求核准程序來設定。  
  
-   它可以設定使用自動發行，其中入口網站會自動發佈要求到通用描述、 探索與整合 (UDDI) 登錄而不需要系統管理員介入。  
  
 下列兩個程序中所述，您也可以指定入口網站中，UDDI 整合功能的幾個其他的設定。  
  
### <a name="to-configure-auto-approval-and-publishing-in-the-esb-management-portal"></a>若要在 ESB 管理入口網站中設定自動核准及發行  
  
1.  請確定您在入口網站使用的 BizTalk Server 系統管理員群組成員的帳戶登入。  
  
2.  指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**登錄設定**開啟入口網站[登錄設定] 頁面](../esb-toolkit/registry-settings-page.md)。  
  
3.  若要啟用自動核准及發行，在頂端的文字方塊中輸入 UDDI 伺服器的 URL **UDDI 詳細資料**的頁面上，然後選取區段**使其自動發佈**核取方塊。  
  
4.  若要停用自動核准及發行，請清除**自動發行**核取方塊。  
  
### <a name="to-configure-e-mail-and-registry-settings-for-the-uddi-integration-features"></a>若要設定電子郵件和登錄設定 UDDI 整合功能  
  
1.  請確定您在入口網站使用的 BizTalk Server 系統管理員帳戶的群組成員的帳戶登入。  
  
2.  指向**Admin**入口網站的主功能表上的索引標籤，然後按一下 [**登錄設定**開啟入口網站[登錄設定] 頁面](../esb-toolkit/registry-settings-page.md)。  
  
3.  編輯程式頂端的文字方塊中的 UDDI 伺服器的 URL **UDDI 詳細資料**頁面區段。 預設 「 UDDI 服務是本機 Microsoft UDDI 服務。  
  
4.  選取**匿名**核取方塊，如果您想要在入口網站中存取的 UDDI 伺服器時，使用匿名驗證。  
  
5.  如果您想要在入口網站以電子郵件時 UDDI 發行通知您要求正在等待核准，請選取**啟用通知**中核取方塊**電子郵件通知**頁面區段。 然後輸入您的電子郵件伺服器、 傳遞電子郵件地址、 適當的 「 寄件者 」 電子郵件地址、 郵件主旨和訊息內文的詳細資料。  
  
6.  輸入系統管理員的連絡人名稱和電子郵件地址 UDDI 的回條要求中的電子郵件訊息**預設設定**頁面區段。  
  
### <a name="to-approve-or-decline-a-registration-request-as-an-administrator"></a>若要核准或拒絕登錄要求，以系統管理員  
  
1.  請確定您登入入口網站使用的 BizTalk Server 系統管理員群組成員的帳戶。  
  
2.  指向**登錄**入口網站的主功能表上的索引標籤，然後按一下 **管理暫止要求**開啟入口網站[管理擱置的要求頁面](../esb-toolkit/manage-pending-requests-page.md)。  
  
3.  若要核准的暫止要求，請按一下**核准**旁該要求清單中的圖示 （核取記號）。  
  
4.  若要拒絕擱置要求時，按一下**拒絕**旁該要求清單中的圖示 （交叉標記）。  
  
5.  若要檢視擱置中要求的詳細資訊，請按一下**檢視詳細資料**圖示 （放大鏡） 若要開啟[登錄詳細資料頁面](../esb-toolkit/registry-details-page.md)。 您可以發佈、 刪除或更新此頁面中的要求。  
  
6.  若要檢閱要求的狀態，並查看先前的要求清單按一下**檢視要求記錄**連結。
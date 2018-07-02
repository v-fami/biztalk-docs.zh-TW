---
title: 自動登錄和核准程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dfd3e72e-e28b-4ee3-bc4a-89ef3f64e6d5
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39dae57d3265ed4e8a383c315276a7e8c510ce37
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968143"
---
# <a name="the-auto-enlist-and-approval-process"></a>自動登錄和核准程序
您可以設定 ESB 管理入口網站來發佈 Microsoft BizTalk Server 端點有兩種：  
  
- 它可以設定核准程序，其中系統管理員必須確認及核准註冊要求。  
  
- 它可以設定使用自動發行，其中入口網站會自動發佈要求到通用描述、 探索與整合 (UDDI) 登錄而不需要系統管理員介入。  
  
  下列兩個程序中所述，您也可以指定幾個其他設定的入口網站中，UDDI 整合功能。  
  
### <a name="to-configure-auto-approval-and-publishing-in-the-esb-management-portal"></a>ESB 管理入口網站中設定自動核准及發行  
  
1.  請確定您在入口網站使用 BizTalk Server 系統管理員群組的成員帳戶登入。  
  
2.  指向**系統管理員**入口網站的主功能表中，索引標籤，然後按一下**登錄設定**以開啟入口網站[登錄設定 頁面](../esb-toolkit/registry-settings-page.md)。  
  
3.  若要啟用自動核准及發行，，請在頂端的文字方塊中輸入您的 UDDI 伺服器的 URL **UDDI 詳細資料**頁面上，然後再選取 區段**使其自動發佈**核取方塊。  
  
4.  若要停用自動核准及發行，請清除**自動發行**核取方塊。  
  
### <a name="to-configure-e-mail-and-registry-settings-for-the-uddi-integration-features"></a>若要設定的 UDDI 整合功能的電子郵件和登錄設定  
  
1.  請確定您在入口網站使用的 BizTalk Server 系統管理員帳戶群組成員的帳戶登入。  
  
2.  指向**系統管理員**入口網站的主功能表中，索引標籤，然後按一下**登錄設定**以開啟入口網站[登錄設定 頁面](../esb-toolkit/registry-settings-page.md)。  
  
3.  編輯您在頂端的文字方塊中的 UDDI 伺服器的 URL **UDDI 細節**頁面區段。 預設的 「 UDDI 服務是本機的 Microsoft UDDI 服務。  
  
4.  選取 [ **Anonymous**如果您想要在入口網站存取的 UDDI 伺服器時，使用匿名驗證] 核取方塊。  
  
5.  如果您想要在入口網站以電子郵件，當 UDDI 發行時通知您要求正在等待核准，請選取**啟用通知**中的核取方塊**電子郵件通知**頁面區段。 然後輸入您的電子郵件伺服器、 傳遞電子郵件地址、 適當的 「 來源 」 電子郵件地址、 郵件主旨和訊息內文的詳細資料。  
  
6.  輸入系統管理員的連絡人名稱和電子郵件地址 UDDI 的回條要求中的電子郵件訊息**預設設定**頁面區段。  
  
### <a name="to-approve-or-decline-a-registration-request-as-an-administrator"></a>若要核准或拒絕系統管理員身分註冊要求  
  
1.  請確定您登入入口網站中使用的 BizTalk Server 系統管理員群組成員的帳戶。  
  
2.  指向**登錄**入口網站的主功能表中，索引標籤，然後按一下**管理暫止要求**以開啟入口網站[管理暫止的要求頁面](../esb-toolkit/manage-pending-requests-page.md)。  
  
3.  若要核准的暫止要求，請按一下**核准**該要求在清單旁的圖示 （核取記號）。  
  
4.  若要拒絕待決要求，按一下**拒絕**該要求在清單旁的圖示 （叉記號）。  
  
5.  若要檢視擱置中要求的詳細資訊，請按一下**檢視詳細資料**圖示 （放大鏡） 來開啟[登錄詳細資料頁面](../esb-toolkit/registry-details-page.md)。 您可以發佈、 刪除或更新此頁面中的要求。  
  
6.  若要檢閱要求的狀態，並查看先前要求的清單，按一下**檢視要求記錄**連結。
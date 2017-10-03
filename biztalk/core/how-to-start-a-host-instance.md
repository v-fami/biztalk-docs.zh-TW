---
title: "啟動主控件執行個體 |Microsoft 文件"
description: "使用 BizTalk 管理 BizTalk Server 中啟動主控件執行個體"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96a4362-2147-4b8e-a270-bf9a17477ba3
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd5cccc48b33dda4b6458f8dfa8f56a84ad3cd62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="start-a-host-instance"></a>啟動主控件執行個體
您可以使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 或 Windows Management Instrumentation (WMI) 來啟動主控件執行個體。 在您新增或停止主控件執行個體之後，必須啟動它，這樣它才能執行，並將訊息路由至 MessageBox 資料庫。  
  
> [!IMPORTANT]
>  您為主控件執行個體指定的服務帳戶應該是相關主控件 Windows 群組的成員。 否則，主控件執行個體在執行階段可能沒有適當的權限或驗證。 此外，基於安全考量，帳戶應該要有最小權限，因為主控件執行個體裝載的協調流程可能會執行潛在的惡意自訂程式碼。  
  
 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。 如需使用 WMI 啟動主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須以「系統管理員」群組及「BizTalk Server 系統管理員」群組的成員身分登入。  
  
 此外，您也必須是下列資料庫所在伺服器的 db_securityadmin SQL Server 資料庫角色及 securityadmin SQL Server 角色的成員：  
  
-   BAM 主要匯入 (BAMPrimaryImport)  
  
-   BizTalk 管理 (BizTalkMgmtDb)  
  
-   BizTalk MessageBox (BizTalkMsgBoxDb) (全部)  
  
-   BizTalk 追蹤 (BizTalk DTADb)  
  
-   規則引擎 (BizTalkRuleEngineDb)  
  
> [!CAUTION]
>  建議您使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 指令碼更新主控件執行個體的帳戶資訊。 這樣可以確保 BizTalk Server 會更新 BizTalk Server 資料庫中的帳戶資訊，並且在資料庫和主控件執行個體之間維持同步的安全性組態。  
  
## <a name="steps"></a>步驟
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主控件執行個體**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要開始，然後按一下 主控件執行個體**啟動**。  
  
     主控件執行個體狀態會變更為**開始擱置**。 主控件執行個體啟動之後，狀態會變更為**執行**。  
  
 在您啟動主控件執行個體之後，您可以停止它，以避免它將訊息遞送至 MessageBox 資料庫。 您必須停止主控件執行個體，才能從指定的電腦移除 BizTalk Server。 如需停止主控件執行個體的詳細資訊，請參閱[如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [新增主控件執行個體](../core/how-to-add-a-host-instance.md)   
 [停止主控件執行個體](../core/how-to-stop-a-host-instance.md)   
 [刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)   
 [修改主控件執行個體屬性](../core/how-to-modify-host-instance-properties.md)
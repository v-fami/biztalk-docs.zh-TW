---
title: 刪除主控件執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35a06480-0962-4bdc-add2-56f979a2f1c9
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 798ea341ef61b15729dd15742eef7701641e7547
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249198"
---
# <a name="delete-a-host-instance"></a>刪除主控件執行個體

## <a name="overview"></a>概觀
您可以使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台或 Windows Management Instrumentation (WMI) 刪除主控件執行個體。 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。 如需使用 WMI 刪除主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 刪除主控件執行個體時，會從關聯的伺服器移除 BizTalk Server 執行階段的執行個體，且會更新 [BizTalk 管理] 資料庫，以從主控件移除該執行個體。  
  
 為避免在刪除主控件執行個體時遺失訊息，BizTalk Server 會在實際移除執行個體之前完成所有處理作業。  
  
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
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要刪除，然後按一下 主控件執行個體**刪除**。  
  
4.  在**確認刪除主控件執行個體**對話方塊中，按一下 **是**。  
  
    > [!NOTE]
    >  若 BizTalk Server 無法刪除主控件執行個體，則會顯示一個對話方塊，您可以在其中強制刪除主控件執行個體。 閱讀所提供的資訊之後, 按**是**刪除主控件執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)   
 [如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)   
 [如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)   
 [如何修改主控件執行個體屬性](../core/how-to-modify-host-instance-properties.md)
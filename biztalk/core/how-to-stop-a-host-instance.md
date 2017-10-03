---
title: "停止主控件執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1f2e0c1-a387-4182-82ef-e25f49ac509b
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 837b08c30263b48ad481c7e03820cfba0b6c0ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="stop-a-host-instance"></a>停止主控件執行個體

## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或 Windows Management Instrumentation (WMI)，來停止主控件執行個體。 您必須停止主控件執行個體，才能從電腦中刪除它或移除 BizTalk Server。 您可以停止已安裝與啟動的主控件執行個體。 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。  
  
 如需使用 WMI 來停止主控件執行個體資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
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
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要停止]，然後按一下 [主控件執行個體**停止**。  
  
     主控件執行個體狀態會變更為**已停止**。  
  
 在您停止主控件執行個體之後，您可以啟動、刪除它或從電腦中移除 BizTalk Server。 如需啟動主控件執行個體的相關資訊，請參閱[如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)。 如需刪除主控件執行個體的詳細資訊，請參閱[如何刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)   
 [如何啟動主控件執行個體](../core/how-to-start-a-host-instance.md)   
 [如何刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)   
 [如何修改主控件執行個體屬性](../core/how-to-modify-host-instance-properties.md)
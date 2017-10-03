---
title: "變更主控件執行個體屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a35ca0c8-89b3-483a-b2fc-c8f43a8864d1
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 859170362ce804db6eff5b0e928998f008d0c2c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="update-host-instance-properties"></a>更新主控件執行個體屬性

## <a name="overview"></a>概觀
您可以使用 BizTalk Server 管理主控台或 Windows Management Instrumentation (WMI) 來修改主控件執行個體。 您可以修改執行主控件執行個體的服務帳戶。 您也可以停用主控件執行個體。 例如，若您想要保留主控件執行個體的設定，但不想將它啟動，您可以停用它。 如需主控件執行個體的詳細資訊，請參閱[主控件執行個體](../core/host-instances.md)。  
  
 信任與不信任的主控件之主控件執行個體無法使用相同的服務帳戶。 若您想要變更主控件執行個體的信任設定，而主控件執行個體使用其他主控件執行個體使用的服務帳戶，您可以執行下列任何一項動作：  
  
-   您可以變更主控件執行個體的服務帳戶，將該主控件執行個體的信任設定變更為新的服務帳戶。  
  
-   您可以將主控件執行個體的服務帳戶變更為其他具有相同信任設定的主控件執行個體所使用的現有服務帳戶。  
  
-   您可以刪除主控件執行個體，然後以不同的信任設定與服務帳戶重新建立它。  
  
> [!CAUTION]
>  您必須更新主控件執行個體的屬性來變更主控件執行個體的認證。 如果您變更對應服務的認證，則您為主控件執行個體指定的服務帳戶必須是主控件上的群組成員。 請不要使用「服務」嵌入式管理單元或「電腦管理」主控台來變更主控件執行個體的認證，否則主控件執行個體可能無法正確運作。  
  
> [!CAUTION]
>  若您變更主控件執行個體的認證，也必須變更對應的 SQL Server 認證。 若您不更新 SQL Server 認證，主控件執行個體將不會正確運作。  
  
 如需使用 WMI 修改主控件執行個體的詳細資訊，請參閱**MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
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
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主控件執行個體**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要修改，然後按一下 主控件執行個體**屬性**。  
  
4.  在**主控件執行個體屬性**對話方塊中，按一下 **設定**修改服務帳戶資訊。  
  
5.  在**登入認證**對話方塊方塊中，輸入帳戶名稱和密碼的帳戶所在主控件執行個體將會執行，然後按**確定**。  
  
6.  在**主控件執行個體屬性**對話方塊中，執行下列命令，，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**主機名稱**|顯示和所選取的伺服器相關聯的主控件名稱。|  
    |**Server**|顯示與所選取的主控件相關聯的伺服器。|  
    |**登入**|顯示將執行主控件執行個體的新服務帳戶之帳戶名稱。|  
    |**設定**|按一下即可顯示**登入認證**對話方塊中，您可以在此輸入的帳戶名稱和密碼將執行主控件執行個體的帳戶。|  
    |**停用主控件執行個體無法啟動**|選取此核取方塊將選取主控件的狀態由啟用變更為停用。 若您不要主控件執行個體啟動，但是要保留其設定時，停用主控件執行個體就非常有用。|  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [新增主控件執行個體](../core/how-to-add-a-host-instance.md)   
 [啟動主控件執行個體](../core/how-to-start-a-host-instance.md)   
 [停止主控件執行個體](../core/how-to-stop-a-host-instance.md)   
 [刪除主控件執行個體](../core/how-to-delete-a-host-instance.md)
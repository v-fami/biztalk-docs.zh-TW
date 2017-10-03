---
title: "如何修改主控件屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5df9d7f-b6c2-4bb7-a845-284e6323e3d6
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a5dac64bb50cf84c0d14277687d1641b6fa536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="update-host-properties"></a>更新主機內容

## <a name="overview"></a>概觀
您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來修改下列主控件屬性：  
  
-   **Windows 群組：** Windows 群組的成員擁有執行主控件的權限依預設此主控件執行個體。 當您為 BizTalk 主控件選取 Windows 使用者群組時，我們建議您建立該主控件專用的新群組。 若您使用現有的群組，請確定該群組所擁有的權限未超過所需的權限。 如需詳細資訊，請參閱[存取控制與資料安全性](../core/access-control-and-data-security.md)。  
  
    > [!NOTE]
    >  如果變更目前所登入使用者的群組成員資格，而該群組也是網域的成員，則應該在完成變更之後登出，然後再重新登入。 不這麼做會導致存取遭到拒絕，因為目前的登入不會反映新的群組成員資格。  
  
-   **主控件追蹤：**至少一個主機群組中的必須追蹤狀況與商務資料。 此選項指出主控件是否載入 BizTalk 追蹤元件，以處理狀況監控與商務資料。  
  
    > [!NOTE]
    >  我們建議您建立至少一個追蹤主控件的主控件執行個體。 若沒有執行中的追蹤主控件之主控件執行個體，則 MessageBox 資料庫會繼續累計資料，之後將導致效能降低。  
  
     執行主控件追蹤的主控件擁有 MessageBox 資料庫中追蹤資料表與 BizTalk 追蹤資料庫的讀取/寫入存取權限。 因此，在執行主控件追蹤的主控件中執行的任何物件，也會擁有這些資料庫資料表的讀取/寫入存取權限。 未執行主控件追蹤的主控件只擁有 MessageBox 資料庫中追蹤資料表的寫入存取權，而沒有 BizTalk 追蹤資料庫的存取權限。  
  
    > [!NOTE]
    >  指定特定的主控件執行主控件追蹤，會對在同一主控件上執行的應用程式效能造成影響。 因此，您可以考慮建立僅「允許主控件追蹤」的專用主控件。  
  
-   **信任的驗證：**您可以指定 BizTalk Server 信任某個主控件。 BizTalk Server 會信任**驗證信任的主控件**將傳送者安全性識別碼 (SSID) 放置在信任的主控件佇列對主應用程式以外的使用者對應的訊息。 如需驗證信任主控件的詳細資訊，請參閱[驗證訊息的傳送者](../core/authenticating-the-sender-of-a-message.md)。  
  
     信任與不信任的主控件之主控件執行個體無法使用相同的服務帳戶。 若您想要變更主控件執行個體的信任設定，而主控件執行個體使用其他主控件執行個體使用的服務帳戶，您可以執行下列任何一項動作：  
  
    -   您可以變更主控件執行個體的服務帳戶，將該主控件執行個體的信任設定變更為新的服務帳戶。  
  
    -   您可以將主控件執行個體的服務帳戶變更為其他具有相同信任設定的主控件執行個體所使用的現有服務帳戶。  
  
    -   您可以刪除主控件執行個體，然後以不同的信任設定與服務帳戶重新建立它。  
  
-   **預設主機群組中：**必須有預設主控件群組中所有的時間。 在協調流程登錄程序期間，會自動使用預設主控件來裝載協調流程，除非使用者明確選取不同的主控件。 第一個建立的主控件會標示為預設主控件。 如需預設主控件的資訊，請參閱[主機](../core/hosts.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須具有以下的使用者權限才能建立主控件、修改主控件屬性和刪除主控件：  
  
-   您必須是「BizTalk Server 系統管理員」群組的成員。 如需新增使用者至 BizTalk Server 系統管理員群組的資訊，請參閱[如何管理 BizTalk Server 系統管理員群組](../core/how-to-manage-the-biztalk-server-administrators-group.md)。  
  
-   在 SQL Server 中您必須具有以下權限：  
  
    -   您必須是 SQL Server 系統管理員，或是 BizTalk 追蹤資料庫 (BizTalk DTADb)、MessageBox 資料庫 (BizTalkMsgBoxDb)，以及 BAM 主要匯入資料庫 (BAMPrimaryImport) 中 db_owner 或 db_securityadmin SQL Server 資料庫角色的成員。  
  
    -   您必須是具有 MessageBox 資料庫之所有電腦上 sysadmin SQL Server 角色的成員，或是所有 MessageBox 資料庫中 db_owner 或 db_ddladmin SQL Server 角色的成員。  
  
## <a name="steps"></a>步驟  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主機**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要修改，然後按一下的主機**屬性**。  
  
4.  在**主控件屬性**對話方塊**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|顯示主控件的名稱。 當您建立主控件時會為它命名。|  
    |**型別**|顯示主控件類型。 您可以將協調流程登錄至內含式主控件，而內含式主控件可以裝載傳送處理常式。 外掛式主控件是在 BizTalk Server 安裝之外作業。|  
  
     **選項。**  
  
    |使用|動作|  
    |--------------|----------------|  
    |**允許主控件追蹤**|選取此核取方塊以指示主控件載入 BizTalk 追蹤元件，以處理狀況監控與商務資料。 若您選取此核取方塊，目前的主控件將會擁有 MessageBox 資料庫中追蹤資料表與追蹤資料庫的讀取/寫入存取權限。 因此，任何在此主控件中執行的物件也將擁有這些資料庫的讀/寫存取權限。 若您清除此核取方塊，主控件將只會擁有 MessageBox 資料庫中追蹤資料表的寫入存取權，而不會擁有追蹤資料庫的存取權。|  
    |**信任的驗證**|選取此核取方塊，以指定 BizTalk Server 應該信任此主控件。|  
    |**僅限 32 位元**|若您希望在 32 位元與 64 位元的伺服器上都以 32 位元建立主控件執行個體程序，請選取此核取方塊。 若您希望在 32 位元伺服器上使用32 位元以及在 64 位元的伺服器上以 64 位元建立主控件執行個體程序，請清除此核取方塊。<br /><br /> **請注意**要變更 32 位元主控件執行個體處理序成 64 位元主控件執行個體程序，刪除主控件的所有執行個體，然後清除**僅 32 位元**核取方塊。 在 64 位元伺服器上建立主控件的執行個體時，會將其建立為 64 位元。|  
    |**將此預設主機群組中**|選取此核取方塊以辨識主控件是預設主控件。 在協調流程登錄程序期間，會自動使用預設主控件來裝載協調流程，除非您明確選取不同的主控件。 若此核取方塊是已選取且不可用，則此主控件為預設值。|  
    |**Windows 群組**|為主控件輸入本機或網域群組。 Windows 群組的成員擁有執行此主控件執行個體的權限。|  
  
5.  在**憑證**索引標籤上，執行下列工作，，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**說明**|為顯示的解密憑證顯示描述。|  
    |**憑證指紋**|顯示私密金鑰憑證的指紋，此私密金鑰憑證用於為此主控件解密輸入訊息。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。|  
    |**移除憑證**|按一下以從主控件移除顯示的解密憑證。|  
    |**瀏覽**|按一下即可顯示**選取憑證**對話方塊中，從您想要使用與主機在本機電腦或其他人憑證存放區選取解密憑證。|  
  
## <a name="see-also"></a>另請參閱  
-  [透過主控件節流將資源使用最佳化](../core/optimizing-resource-usage-through-host-throttling.md)   
-  [節流設計建議](../core/throttling-design-recommendations.md)   
-  [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
-  [如何建立新的主機](../core/how-to-create-a-new-host.md)   
-  [如何刪除主控件](../core/how-to-delete-a-host.md)   
-  **MSBTS_Host (WMI)**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
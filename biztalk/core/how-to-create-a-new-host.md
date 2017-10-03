---
title: "建立新的主機 |Microsoft 文件"
descriptions: Use BizTalk Administration to create a new host in BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 811e6e57-5c37-471a-aff4-5b2b68c367b1
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 700f0bb43a4f31b76819e7aca6fe5895cc2b6ab6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-new-host"></a>建立新的主機
BizTalk 主控件是配接器處理常式、接收位置 (包括管線)，以及協調流程等項目的邏輯容器。 我們建議您使用不同的主控件來處理、接收和傳送訊息，而且也請針對信任和非信任項目使用不同的主控件，以便實行安全性措施並改善主控件的管理性。 您只可以在每一部 BizTalk Server 上安裝一個主控件執行個體。 如需主控件的詳細資訊，請參閱[主機](../core/hosts.md)。  
  
 使用 Windows Management Instrumentation (WMI) 來建立新的主控件的相關資訊，請參閱**MSBTS_Host (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="prerequisites"></a>必要條件  
 您必須具有以下的使用者權限才能建立主控件、修改主控件屬性和刪除主控件：  
  
-   您必須是「BizTalk Server 系統管理員」群組的成員。  
  
-   在 SQL Server 中您必須具有以下權限：  
  
    -   您必須是 SQL Server 系統管理員，或是 BizTalk 追蹤資料庫 (BizTalk DTADb)、MessageBox 資料庫 (BizTalkMsgBoxDb)，以及 BAM 主要匯入資料庫 (BAMPrimaryImport) 中 db_owner 或 db_securityadmin SQL Server 資料庫角色的成員。  
  
    -   您必須是具有 MessageBox 資料庫之所有電腦上 sysadmin SQL Server 角色的成員，或是所有 MessageBox 資料庫中 db_owner 或 db_ddladmin SQL Server 角色的成員。  
  
## <a name="steps"></a>步驟
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主機**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下**主機**，按一下 **新增**，然後按一下 **主機**。  
  
4.  在**主控件屬性**對話方塊**一般**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|顯示主控件的名稱。 當您建立主控件時會為它命名。 主控件名稱的長度不能超過 80 個字元。|  
    |**型別**|顯示主控件類型。 內含式主控件可以裝載協調流程、特定傳送處理常式和接收處理常式。 外掛式主控件是 BizTalk Server 外部的程序界限，而且特定傳送和接收處理常式需要此主控件。 您可以將協調流程登錄至內含式主控件，而內含式主控件可以裝載傳送或接收處理常式。|  
  
     **選項。**  
  
    |使用|動作|  
    |--------------|----------------|  
    |**允許主控件追蹤**|選取這個核取方塊，指示主控件將處理狀況監控和商務資料。 若您選取此核取方塊，則目前的主控件將擁有 MessageBox 資料庫中追蹤資料表與 BizTalk 追蹤資料庫的讀/寫權限。 因此，任何在此主控件中執行的物件也將擁有這些資料庫的讀/寫存取權限。 若您清除此核取方塊，主控件將只會擁有 MessageBox 資料庫中追蹤資料表的寫入存取權，而不會擁有 BizTalk 追蹤資料庫的存取權。|  
    |**信任的驗證**|選取此核取方塊，以指定 BizTalk Server 應該信任此主控件。|  
    |**僅限 32 位元**|若您希望在 32 位元與 64 位元的伺服器上都以 32 位元建立主控件執行個體程序，請選取此核取方塊。 若您希望在 32 位元伺服器上使用32 位元以及在 64 位元的伺服器上以 64 位元建立主控件執行個體程序，請清除此核取方塊。|  
    |**將此預設主機群組中**|選取此核取方塊以辨識主控件是預設主控件。 除非您明確選取不同的主控件，否則建立的連接埠和協調流程會自動使用預設的主控件來裝載協調流程。 若此核取方塊是已選取且不可用，則此主控件為預設值。|  
    |**Windows 群組**|為主控件輸入本機或網域群組。 Windows 群組的成員擁有執行此主控件執行個體的權限。|  
  
5.  在**憑證**索引標籤上，執行下列工作，，然後按一下**確定**:  
  
    |使用|動作|  
    |--------------|----------------|  
    |**一般名稱**|為顯示的解密憑證顯示描述。|  
    |**憑證指紋**|顯示私密金鑰憑證的指紋，此私密金鑰憑證用於為此主控件解密輸入訊息。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。|  
    |**移除憑證**|按一下以從主控件移除顯示的解密憑證。|  
    |**瀏覽**|按一下即可顯示**Windows 安全性**對話方塊，其中從目前的使用者或您想要使用與主機的個人存放區選取解密憑證。|  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)   
 [修改主控件屬性](../core/how-to-modify-host-properties.md)   
 [刪除主控件](../core/how-to-delete-a-host.md)
---
title: "如何復原 BizTalk 群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1010e55-7e3d-4565-8604-ea652ea4da8c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: deaf3ddae7d7351d53c5cd46b7d48633e0271a3d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-recover-the-biztalk-group"></a>如何復原 BizTalk 群組
在系統復原程序中，您必須將 BizTalk Server 重新加入現有的 BizTalk 群組。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「系統管理員」群組成員的身分登入，才能執行此程序。  
  
 如果您要復原的是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition，必須下載能夠協助復原伺服器的指令碼。 下載[RestoreConfig.vbe](http://go.microsoft.com/fwlink/?LinkID=195799)。  
  
### <a name="to-recover-the-biztalk-group-standard-edition"></a>復原 BizTalk 群組 (Standard Edition)  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  在命令提示字元中，輸入：  
  
     **RestoreConfig.vbe***\<SavedConfigXML  \>*  
  
     其中 *\<SavedConfigXML\>* 是完整路徑和儲存的組態檔的檔名。  
  
     上述命令應該會結束且不顯示任何錯誤。  
  
    > [!NOTE]
    >  若要復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]64 位元電腦上的 Standard Edition，您必須執行**RestoreConfig.vbe**從 32 位元命令提示字元，它可以更新 32 位元登錄。 若要開啟 32 位元命令提示字元，請按一下**啟動**，按一下**執行**，型別**c:\windows\syswow64\cmd.exe**，然後按一下**確定**。  
  
    > [!NOTE]
    >  失敗電腦的名稱會包含在儲存的組態檔中。 您要還原至的電腦必須具有該相同名稱。 您必須在具有該名稱的電腦上執行上述指令碼。 不過，您可以在儲存的組態檔中變更失敗電腦的名稱。 如果這樣做，您就可以在具有不同名稱的電腦上執行上述指令碼。  
  
### <a name="to-recover-the-biztalk-group-developer-edition-or-enterprise-edition"></a>復原 BizTalk 群組 (Developer Edition 或 Enterprise Edition)  
  
1.  按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 組態**。  
  
2.  在[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，在主控台樹狀目錄中，按一下**群組**。  
  
3.  在 [詳細資料] 窗格中，選取**加入現有的 BizTalk 群組**，然後指定適當的遠端 BizTalk 管理 (BizTalkMgmtDb) 資料庫。  
  
4.  按一下 [套用組態]。  
  
5.  按一下**檔案**，然後按一下 **結束**。  
  
## <a name="see-also"></a>請參閱  
 [復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md)
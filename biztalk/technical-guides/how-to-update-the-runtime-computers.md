---
title: 如何更新執行階段電腦 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 576a7065-04b6-436c-acf9-28c8d6e40107
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fff5c5ec4c965b9dbdaaf5d876ca0943a32be96
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993295"
---
# <a name="how-to-update-the-runtime-computers"></a>如何更新執行階段電腦
在目的系統[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦設有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態精靈，在生產環境中執行的生產環境 BizTalk 群組的一部分。 嚴重損壞修復環境中還原生產 BizTalk 群組時，必須在每個更新設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓它指向嚴重損壞修復的執行階段電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]個執行個體時它會嘗試連接到已還原生產環境的 BizTalk 群組。 在目的系統還原的 BizTalk 群組之後，使用下列程序來更新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦。  
  
### <a name="to-update-the-biztalk-server-runtime-computers"></a>若要更新 BizTalk Server 執行階段電腦  
  
1. 複製已編輯的 SampleUpdateInfo.xml 檔案 \Program Files\Microsoft 每一部 32 位元 BizTalk 伺服器上的 BizTalk Server\Schema\Restore 目錄或 \Program Files (x86) \Microsoft BizTalk Server\Bins32\Schema\Restore 目錄上每個 64 位元 BizTalk目的系統中的伺服器。  
  
2. 每個 BizTalk 伺服器上，開啟命令提示字元。 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
   > [!NOTE]  
   >  在 64 位元電腦，您必須開啟 64 位元命令提示字元。  
  
3. 在命令提示中，巡覽至 \Program Files\Microsoft BizTalk Server\Schema\Restore （32 位元的電腦上） 或 \Program 檔案 (x86) \Microsoft BizTalk Server\Bins32\Schema\Restore （64 位元的電腦上），並輸入下列命令：  
  
   ```  
   cscript UpdateRegistry.vbs SampleUpdateInfo.xml  
   ```  
  
4. 啟用並重新啟動所有 BizTalk 主控件執行個體和 BizTalk server 上的所有其他 BizTalk 服務在目的系統。  
  
5. 每個 BizTalk 伺服器上重新啟動 WMI 目的系統中。 按一下 **開始**，按一下**執行**，型別**services.msc**，然後按一下 **確定**。 在  **Services** MMC 嵌入式管理單元，以滑鼠右鍵按一下**Windows Management Instrumentation** ，然後選取**重新啟動**。  
  
6. 每個 BizTalk 伺服器上，開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**移除**。  
  
7. 以滑鼠右鍵按一下**BizTalk Server 2010 管理**，選取**連接到現有的群組**、 選取 SQL Server 資料庫執行個體和資料庫對應至 BizTalk 管理資料庫的名稱BizTalk 群組，然後按一下**確定**。  
  
   > [!NOTE]
   >  在更新之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦，您可能也需要更新**SSO 伺服器名稱**中所示**群組屬性**對話方塊中可用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 若要更新**SSO 伺服器名稱**，啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下以展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理，以滑鼠右鍵按一下**BizTalk 群組**節點，然後選取**屬性**以顯示**一般**索引標籤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 然後，在**SSO 伺服器名稱**文字方塊中，輸入此電腦將會使用存取配接器的組態資訊，然後按一下 企業單一登入伺服器名稱**確定**。 這是用來連接到 SSO 資料庫之 SSO 伺服器的名稱。  
  
8. 重新啟動每個 BizTalk 執行階段伺服器上的下列 Windows 服務：  
  
   -   企業 SSO 服務  
  
   -   規則引擎更新服務  
  
   -   BizTalk 主控件執行個體  
  
## <a name="see-also"></a>另請參閱  
 [復原執行階段電腦](../technical-guides/recovering-the-runtime-computers.md)
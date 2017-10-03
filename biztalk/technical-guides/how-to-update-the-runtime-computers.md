---
title: "如何更新執行階段電腦 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 576a7065-04b6-436c-acf9-28c8d6e40107
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0fc6423a8918237362636f26322b145a0cbcf26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-runtime-computers"></a>如何更新執行階段電腦
在目的系統[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定執行階段電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態精靈，在實際執行環境中執行的生產環境 BizTalk 群組的一部分。 嚴重損壞修復環境中還原的實際執行的 BizTalk 群組時，必須在每個更新設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓它指向嚴重損壞修復的執行階段電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]時若嘗試連接到已還原的執行個體實際執行的 BizTalk 群組。 在目的系統還原 BizTalk 群組之後，使用下列程序來更新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦。  
  
### <a name="to-update-the-biztalk-server-runtime-computers"></a>若要更新 BizTalk Server 執行階段電腦  
  
1.  將已編輯的 SampleUpdateInfo.xml 檔案複製至 files\microsoft [!INCLUDE[prague](../includes/prague-md.md)]\Schema\Restore 目錄，每個 32 位元的 BizTalk server 上或 \Program Files (x86) \Microsoft [!INCLUDE[prague](../includes/prague-md.md)]\Bins32\Schema\Restore 上每個 64 位元的目錄目的系統中的 BizTalk server。  
  
2.  每個 BizTalk 伺服器上，開啟命令提示字元。 按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
    > [!NOTE]  
    >  在 64 位元電腦上，您必須開啟 64 位元命令提示字元。  
  
3.  在命令提示中，瀏覽至 files\microsoft [!INCLUDE[prague](../includes/prague-md.md)]\Schema\Restore （32 位元的電腦上） 或 \Program Files (x86) \Microsoft [!INCLUDE[prague](../includes/prague-md.md)]\Bins32\Schema\Restore （64 位元的電腦上），然後輸入這個命令：  
  
    ```  
    cscript UpdateRegistry.vbs SampleUpdateInfo.xml  
    ```  
  
4.  啟用並重新啟動所有 BizTalk 主控件執行個體和 BizTalk 伺服器上其他所有的 BizTalk 服務在目的系統。  
  
5.  每個 BizTalk 伺服器上重新啟動 WMI 目的系統中。 按一下**啟動**，按一下 **執行**，型別**services.msc**，然後按一下 **確定**。 在**服務**MMC 嵌入式管理單元，以滑鼠右鍵按一下**Windows Management Instrumentation**選取**重新啟動**。  
  
6.  每個 BizTalk 伺服器上，開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**移除**。  
  
7.  以滑鼠右鍵按一下**BizTalk Server 2010 管理**，選取**連接至現有的群組**、 選取的 SQL Server 資料庫執行個體和資料庫對應至 BizTalk 管理資料庫的名稱BizTalk 群組，然後按一下**確定**。  
  
    > [!NOTE]  
    >  在更新之後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦，您可能也需要更新**SSO 伺服器名稱**示**群組內容**對話方塊可以在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 若要更新**SSO 伺服器名稱**，啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下以展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理，以滑鼠右鍵按一下**BizTalk 群組**節點，然後選取**屬性**顯示**一般** 索引標籤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 然後，在**SSO 伺服器名稱**文字方塊中，輸入此電腦將會使用存取配接器的組態資訊，然後按一下 企業單一登入伺服器的名稱**確定**。 這是用來連接到 SSO 資料庫之 SSO 伺服器的名稱。  
  
8.  重新啟動每個 BizTalk 執行階段伺服器上的下列 Windows 服務：  
  
    -   企業 SSO 服務  
  
    -   規則引擎更新服務  
  
    -   BizTalk 主控件執行個體  
  
## <a name="see-also"></a>另請參閱  
 [復原執行階段電腦](../technical-guides/recovering-the-runtime-computers.md)
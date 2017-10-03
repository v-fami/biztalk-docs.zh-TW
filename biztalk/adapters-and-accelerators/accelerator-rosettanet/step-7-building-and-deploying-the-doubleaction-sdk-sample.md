---
title: "步驟 7： 建置與部署 DoubleAction SDK 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, building solutions
- deploying, solutions
- building solutions
- double action tutorial, deploying solutions
ms.assetid: f67f8aee-1004-48ee-a6fd-881097382888
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b503f423d736d9c5f08c7d04a84110a85564d11d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-building-and-deploying-the-doubleaction-sdk-sample"></a>步驟 7： 建置與部署 DoubleAction SDK 範例
DoubleAction.odx 範例會顯示如何實作協調流程，自動為雙向動作「夥伴介面程序」(PIP) 0C2、0C4、3A2 和 3A4 產生回應。 您可以擴充此範例專案來支援其他的雙向動作 PIP。  
  
 您將使用此範例，在 Fabrikam 使用四種 PIP 中任一種產生要求時，自動傳送回應給 Fabrikam。  
  
### <a name="to-build-and-initialize-the-doubleaction-sample"></a>建置與初始化 DoubleAction 範例  
  
1.  在 Contoso 電腦上的命令提示字元視窗中，移至下列資料夾：   
    *\<磁碟機 >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for rosettanet\sdk\pipautomation\doubleaction 中\\。  
  
    > [!NOTE]
    >  執行安裝程式前，在 [記事本] 中開啟 DoubleAction.sql 檔案 (位於上述資料夾)。 在**檔案**功能表上，按一下 **存**。 在**編碼**方塊中，選取**ANSI**從下拉式清單，然後按一下**儲存**。 按一下**是**覆寫現有檔案。  
  
2.  如果您的 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 安裝是在 SQL Server 2008 R2/2008 SP1 上執行，請執行相同資料夾中的 setupx64.bat。 這個批次檔將會執行下列動作：  
  
    -   在 BTARNDATA 資料庫中建立 SQL 預存程序 (`PipAutomationGetAction`)，以便從 MessagesToLOB 資料表擷取動作訊息。  
  
    -   編譯 HeaderHelper .NET 專案，並在全域組件快取中註冊組件。  
  
    -   建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] SQL 接收埠 (MessagesToLOB_Receive_Port)。  
  
    -   啟用接收位置 (MessagesToLOB_Receive_Location)。  
  
    -   編譯及部署雙向動作 PIPAutomation 協調流程 (DoubleAction.odx)。  
  
    -   繫結並啟動 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 協調流程。  
  
        > [!NOTE]
        >  範例在編譯時會出現一些警告。 您可以忽略這些警告。  
  
        > [!NOTE]
        >  確認 DoubleAction.odx 已繫結至**MessagesToLOB_Receive_Port**，並已啟動協調流程。  
  
3.  在[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]管理主控台中，展開  **BizTalk 群組**，**應用程式**，和**BizTalk Application 1**節點。 按一下**協調流程**節點。 以滑鼠右鍵按一下**DoubleAction**協調流程，然後再按一下**屬性**。 在 屬性 對話方塊中，按一下 **繫結** 節點，並將其設定**主機**至**BizTalkServerApplication**並設定**接收埠**至**MessageToLOB_ReceivePort**。 按一下 **[確定]**。 以滑鼠右鍵按一下**DoubleAction**協調流程，然後再按一下**啟動**。  
  
## <a name="see-also"></a>另請參閱  
 [建立與設定 Fabrikam 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)
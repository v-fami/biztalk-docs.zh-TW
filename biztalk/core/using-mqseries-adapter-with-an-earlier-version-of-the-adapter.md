---
title: "以舊版配接器使用 MQSeries 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, compatibility
ms.assetid: 278a13ff-8e46-4af4-a76e-b6d4aad5b768
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba635b9bc4569f17418fc925c54c64d0fdc67461
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-mqseries-adapter-with-an-earlier-version-of-the-adapter"></a>以舊版配接器使用 MQSeries 配接器
[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]、[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 和 [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] 版本的 MQSeries 配接器都可與 Windows 上相同的遠端 WebSphere MQ Server 搭配使用。 這是可能的，因為與 MQSeries 配接器搭配使用的下列版本 COM+ 應用程式，可同時存在相同的 WebSphere MQSeries 電腦上：  
  
-   **MQSAgent (MQSAgent2) COM + 應用程式**MQSeries 配接器搭配使用[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]。  
  
-   **MQSAgent COM + 應用程式**MQSeries 配接器搭配使用[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)]。  
  
-   **MQHelper COM + 應用程式**MQSeries 配接器搭配使用[!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)]。  
  
> [!NOTE]
>  設定這些 COM+ 應用程式並存的安裝時，請確定沒有任何 COM+ 應用程式設為使用相同的 MQSeries 佇列。  
  
> [!IMPORTANT]
>  MQSeries Adapter COM+ 應用程式與舊版 MQSeries Adapter COM+ 應用程式的 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 版並存安裝只有在 WebSphere MQSeries 電腦上未安裝舊版 BizTalk Server 時才支援。  
  
### <a name="to-install-the-biztalk-server-2006-version-of-the-mqseries-adapter-com-application-on-a-websphere-mqseries-computer-that-is-running-an-earlier-version-of-the-mqseries-adapter-com-application"></a>在執行舊版 MQSeries Adapter COM+ 應用程式的 WebSphere MQSeries 電腦上安裝 MQSeries Adapter COM+ 應用程式的 BizTalk Server 2006 版  
  
1.  從 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 光碟上的 \Platform\BootStrap\ 目錄執行 Bootstrap.msi，將相依檔案 MSVCR80.dll 和 MSVCP80.dll 複製到 WebSphere MQSeries 電腦中。  
  
2.  從 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 光碟上的 \Msi\Program Files\ 目錄將 MQSAgent.dll 複製到 WebSphere MQSeries 電腦中。  
  
    > [!NOTE]
    >  如果您打算使用 MQSAgent 追蹤公用程式，則從此目錄一併將 MQSTrace.cmd 檔複製到 WebSphere MQSeries 電腦上。 如需 MQSAgent 追蹤公用程式請參閱[使用追蹤工具分析 MQSeries 配接器錯誤](../core/analyzing-mqseries-adapter-errors-with-the-trace-tools.md)。  
  
3.  在 WebSphere MQSeries 電腦上執行 regsvr32 mqsagent.dll，以便在 MQSAgent.dll 中手動註冊元件：  
  
    ```  
    regsvr32 MQSAgent.dll  
    ```  
  
    > [!NOTE]
    >  從您將 MQSAgent.dll 複製到其中的同一個目錄執行此命令。  
  
4.  為 MQSAgent 元件建立新的 COM+ 應用程式：  
  
    -   以滑鼠右鍵按一下 COM + 應用程式中，按一下**新增**，**應用程式**顯示**COM + 應用程式安裝精靈**按一下**下一步**。  
  
    -   按一下**建立空白的應用程式**。  
  
    -   輸入名稱**MQSAgent2**，保留預設選項為**伺服器應用程式**啟用，然後按一下**下一步**。  
  
    -   選取的選項**這位使用者**，輸入適當的帳戶資訊，然後按一下**下一步**。  
  
        > [!NOTE]
        >  在適當的 IBM WebSphere MQ 佇列上，此帳戶應該具備「連線」與「放置」以及/或「取得」權限。  
  
    -   按一下**下一步**在 [新增**應用程式角色**] 對話方塊。  
  
    -   按一下**下一步**上**將使用者加入角色** 對話方塊。  
  
    -   按一下 **[完成]**。  
  
5.  新增 MQSAgent.dll 元件至 MQSAgent2 COM+ 應用程式：  
  
    -   按一下以展開**MQSAgent2** COM + 應用程式。  
  
    -   以滑鼠右鍵按一下**元件**按一下**新增**，**元件**啟動 COM + 元件安裝精靈，然後按一下**下一步**。  
  
    -   按一下**安裝新元件**，瀏覽至 MQSAgent.dll 檔案，然後按一下**開啟**。  
  
    -   按 **[下一步]**，再按一下 **[完成]**。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MQSeries 配接器](../core/using-the-mqseries-adapter.md)
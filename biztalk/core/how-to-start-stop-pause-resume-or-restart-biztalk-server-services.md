---
title: 若要重新啟動服務，或關閉的步驟 |Microsoft Docs
description: 啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務，或關閉 BizTalk Server 電腦
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d6449ba-2892-49c6-a697-847608d10ec5
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b83e7573117749ce78789de0ba21ef63ebed217
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987887"
---
# <a name="restart-biztalk-services-or-shut-down-the-biztalk-server"></a>重新啟動 BizTalk 服務，或關閉 BizTalk Server

您可啟動、停止、暫停、繼續或重新啟動下表列出的 BizTalk Server 服務：  
  
|[屬性]|描述|啟動類型|相依性|  
|----------|-----------------|------------------|------------------|  
|BizTalk 服務 BizTalk 群組：  *\<BizTalkServerApplication\>*|提供 BizTalk Server 應用程式服務。|Automatic|企業單一登入 (SSO) 服務<br />-事件記錄檔<br />-遠端程序呼叫 (RPC)|  
|企業單一登入服務|提供單一登入服務給企業應用程式。|Automatic|SQL Server 在本機安裝：<br /><br /> -COM + 系統應用程式<br />-遠端程序呼叫 (RPC)<br />SQL Server (MSSQLSERVER)<br /><br /> SQL Server 在遠端安裝：<br /><br /> -COM + 系統應用程式<br />-遠端程序呼叫 (RPC) 無|  
|規則引擎更新服務|通知使用者有關原則的部署或解除部署。|Automatic|無|  
  
 
## <a name="start-stop-pause-resume-or-restart-a-biztalk-server-service"></a>啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務  
 您可以啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務，使用 Services.msc，或使用命令提示字元。

### <a name="prerequisites"></a>必要條件  
 若要執行此程序，您必須是本機電腦的系統管理員群組的成員，或者必須已經被委派適當的授權。 若電腦已加入網域中，則 Domain Admins 群組的成員將可執行此程序。 最佳的安全作法是考慮使用 [執行身分] 來執行此程序。 
  
### <a name="use-services-in-control-panel"></a>使用控制台中的服務  
  
1.  開啟 [服務]。 按一下 **開始**，按一下**執行**，然後輸入**services.msc**。  
  
2.  以滑鼠右鍵按一下適當的 BizTalk Server 服務，然後按一下 **開始**，**停止**，**暫停**，**繼續**，或**重新啟動**。  
  
### <a name="use-a-command-prompt"></a>使用命令提示字元  
  
1.  從 [開始] 功能表中，以滑鼠右鍵按一下**命令提示字元**，選取**詳細**，然後選取**系統管理員身分執行**
  
2.  輸入下列命令，其中何處*ServiceName*是您想要啟動、 停止、 暫停或繼續的 BizTalk Server 服務名稱：  
  
    -   若要啟動服務，請輸入：  
  
         **net start** *ServiceName*  
  
    -   若要停止服務，請輸入：  
  
         **net stop** *ServiceName*  
  
    -   若要暫停服務，請輸入：  
  
         **net pause** *ServiceName*  
  
    -   若要繼續服務，請輸入：  
  
         **net 繼續** *ServiceName*  

    |BizTalk 服務|ServiceName|  
    |---|---|  
    |BizTalk 服務 BizTalk 群組：BizTalkServerApplication|btssvc$biztalkserverapplication|  
    |企業單一登入服務|Entsso|  
    |規則引擎更新服務|ruleengineupdateservice|
  
## <a name="shut-down-biztalk-server"></a>關閉 BizTalk Server  

### <a name="prerequisites"></a>必要條件  
-   是您想要關閉的 BizTalk server 上的本機 administrators 群組的成員帳戶登入。 這是必要的因此您可以停止服務。  
-   使用 BizTalk Server 系統管理員群組或 BizTalk Server 操作員群組的成員帳戶登入。 

### <a name="task-overview"></a>工作概觀
1. 停用接收位置，並停止協調流程，並且透過對每個作用中的應用程式中執行部分停止傳送埠。 只有當您想要移除或重新部署應用程式，您應該執行完全停止。 如需詳細資訊，請參閱 <<c0> [ 如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)。  
  
2. 停止主控件執行個體。 如需詳細資訊，請參閱 <<c0> [ 如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)。  
  
3. 關閉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務。 請參閱**如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server Services** （在本主題中）。
  
4. 關閉向下網際網路資訊服務 (IIS)，或停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式集區和網站。 如果您要關閉伺服器完全您可以略過此步驟。 如果您停止[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]進行維護，或以部署或解除部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中，您應該執行此步驟。 當您停止 Web 站台和應用程式集區相關聯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，其他與 IIS 相關處理程序將會繼續執行。  
  
    進行此步驟取決於您所使用的 IIS 版本某種程度。 IIS 6 可讓您停止應用程式集區和網站。 您也可以使用 IIS 6 停止 IIS 管理服務，關閉所有的 IIS 活動，包括應用程式集區和網站。 IIS 7.0 與 IIS 6.0 中，更接近模組化而且沒有任何可用來停止所有 IIS 7.0 的活動，因此您必須個別都停止網站和應用程式集區的單一參數。  
  
    如需應用程式集區和虛擬應用程式 （網站和 Web 服務） BizTalk Server 所使用的清單，請參閱 <<c0> [ 設定 BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)。  
  
   如需啟動和停止應用程式集區，在 IIS 中的資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkID=140513 ](http://go.microsoft.com/fwlink/?LinkID=140513)。  
  
   啟動和停止中 IIS Web 伺服器的詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=140695 ](http://go.microsoft.com/fwlink/?LinkId=140695)。  
  
## <a name="see-also"></a>另請參閱  
 [如何啟動和停止 BizTalk 應用程式](../core/how-to-start-and-stop-a-biztalk-application.md)   
 [如何停止主控件執行個體](../core/how-to-stop-a-host-instance.md)   
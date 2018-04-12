---
title: 網際網路對向 Web 服務和 WCF 服務發佈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7553608-f57a-470e-91d4-75504b3fd52b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e466c4fc2a5f83f5a8445601235b53f44404a912
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="publishing-internet-facing-web-services-and-wcf-services"></a>發行的網際網路對向 Web 服務和 WCF 服務
您可以使用多種發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和到網際網路的 WCF 服務：  
  
-   周邊網路 （也也稱為 DMZ 和遮蔽式子網路） 中使用反向 proxy 規則。  
  
-   將執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將 Web 服務或 WCF 服務發佈至周邊網路的網域。  
  
-   使用 BizTalk Server 雲端推手功能來發佈 Web 服務或 WCF 服務，為 Azure AppFabric 服務匯流排轉送端點。  
  
## <a name="using-a-reverse-proxy"></a>使用反向 Proxy  
 這是已發行的傳統方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務。 在周邊網路中使用反向 proxy 規則而毋需有 BizTalk 伺服器位於周邊網路中。 反向 proxy 規則只是轉送給 HTTP 與 SOAP 要求從周邊網路的電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內部網路網域中。  
  
 如需有關使用反向 proxy 的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：  
  
-   [「 範例架構： HTTP 和 SOAP 配接器 」](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339)。  
  
-   [「 範例 TMA: HTTP 和 SOAP 配接器 」](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340)。  
  
-   ["Large Distributed Architecture"](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341)。  
  
## <a name="using-computers-running-biztalk-server-in-the-perimeter-network"></a>使用周邊網路中執行 BizTalk Server 的電腦  
 這不是慣用的方法發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務或網際網路的 WCF 服務，因為它需要執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]位於周邊網路中。 不過，無法在周邊網路中使用反向 proxy 時，您可以使用這個方法。  
  
 這個方法需要登記在與內部網路網域的單向信任周邊網路網域 （但內部網路網域不信任周邊網路網域）。 IIS 應用程式集區必須處於 「 BizTalk 外掛式主控件使用者 」 網域群組的內部網路網域帳戶底下執行 Web 服務或在周邊網路網域中的 WCF 服務主機。 這可讓應用程式集區 發佈訊息至必要的權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。  
  
 您必須配合這種情形在防火牆中開啟特定連接埠。 如需必要的連接埠的詳細資訊，請參閱[「 連接埠的接收和傳送伺服器 」](http://go.microsoft.com/fwlink/?LinkId=153342) (http://go.microsoft.com/fwlink/?LinkId=153342) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。  
  
## <a name="exposing-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services"></a>公開使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式  
 請參閱文章[使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式公開](http://go.microsoft.com/fwlink/?LinkID=204700)(http://go.microsoft.com/fwlink/?LinkID=204700) 如需有關將 BizTalk 應用程式公開為 WCF 服務在雲端上。  
  
## <a name="see-also"></a>請參閱  
 [發佈 Web Services1 規劃](../technical-guides/planning-for-publishing-web-services1.md)
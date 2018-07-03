---
title: 網際網路對向 Web 服務和 WCF 服務發佈 |Microsoft Docs
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
ms.openlocfilehash: 32a0478e43f87dfbf29f736fde062c67fb4a94cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009199"
---
# <a name="publishing-internet-facing-web-services-and-wcf-services"></a>發佈網際網路對向 Web 服務和 WCF 服務
您可以使用多個方法發佈[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和網際網路的 WCF 服務：  
  
- 周邊網路 （也也稱為 DMZ 和遮蔽式子網路） 中使用反向 proxy 規則。  
  
- 將執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將 Web 服務或 WCF 服務發佈至周邊網路的網域。  
  
- 使用 BizTalk Server 的雲端啟用程式功能，將 Web 服務或 WCF 服務發佈為 Azure AppFabric 服務匯流排轉送端點。  
  
## <a name="using-a-reverse-proxy"></a>使用反向 Proxy  
 這已發行的傳統方法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務和 WCF 服務。 在周邊網路中使用反向 proxy 規則，而毋需已位於周邊網路中的 BizTalk server。 反向 proxy 規則只是轉送 HTTP 與 SOAP 要求從周邊網路到執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內部網路網域中。  
  
 如需使用反向 proxy 的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：  
  
-   [「 架構的範例： HTTP 和 SOAP 配接器"](http://go.microsoft.com/fwlink/?LinkId=153339) (http://go.microsoft.com/fwlink/?LinkId=153339)。  
  
-   [「 範例 TMA: HTTP 和 SOAP 配接器"](http://go.microsoft.com/fwlink/?LinkId=153340) (http://go.microsoft.com/fwlink/?LinkId=153340)。  
  
-   [「 大型分散式架構 」](http://go.microsoft.com/fwlink/?LinkId=153341) (http://go.microsoft.com/fwlink/?LinkId=153341)。  
  
## <a name="using-computers-running-biztalk-server-in-the-perimeter-network"></a>使用周邊網路中執行 BizTalk Server 的電腦  
 這不是慣用的方法，供發行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Web 服務或 WCF 服務到網際網路，因為它需要執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]位於周邊網路中。 不過，無法使用周邊網路中的反向 proxy 時，您可以使用這種方法。  
  
 此方法需要周邊網路網域，在與內部網路網域的單向信任中登記 （但內部網路網域不信任周邊網路網域）。 在 「 BizTalk 外掛式主控件使用者 」 網域群組的內部網路網域帳戶，則必須執行的 Web 服務或周邊網路網域中的 WCF 服務裝載集區的 IIS 應用程式。 這可讓應用程式集區 發佈訊息，以將必要權限[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]MessageBox 資料庫。  
  
 您必須在防火牆，以配合這一點，來開啟特定連接埠。 如需有關必要的連接埠的詳細資訊，請參閱[連接埠的接收和傳送伺服器 >](http://go.microsoft.com/fwlink/?LinkId=153342) (<http://go.microsoft.com/fwlink/?LinkId=153342>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件。  
  
## <a name="exposing-biztalk-applications-on-the-cloud-using-appfabric-connect-for-services"></a>公開使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式  
 請參閱文章[公開使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=204700)(http://go.microsoft.com/fwlink/?LinkID=204700)如需詳細資訊，請為在雲端上的 WCF 服務公開的 BizTalk 應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [發佈 Web Services1 規劃](../technical-guides/planning-for-publishing-web-services1.md)
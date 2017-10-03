---
title: "向外延展傳送主控件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosts, sending
- FTP adapters, high availability
- EDI adapters, high availability
- hosts, high availability
- hosts, availability
- Windows SharePoint Services adapters, high availability
- scaling, hosts
- hosts, clustering
- scaling, adapters
- high availability, hosts
- clustering, hosts
- MSMQ adapters, high availability
- hosts, planning
- hosts, scaling
- adapters, scaling
ms.assetid: a3d79e0b-8c1e-471c-88e2-623600dfd81a
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1fb8ac3fe3752702ed3e1aa2795e521d7173618
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-sending-hosts"></a>向外擴充的傳送主控件
向外擴充的傳送主控件可確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的傳送功能為高度可用。 若您將多部電腦新增至傳送訊息的主控件，則可執行多個傳送主控件執行個體以獲得備援與高可用性。  
  
 下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的部署，它有兩部執行傳送主控件執行個體的電腦，可為傳送主控件提供高可用性。 請注意，在此圖中接收和處理主控件不是高度可用。  
  
 ![調整 &#45; Out 傳送主機](../core/media/tdi-ha-scalesend.gif "TDI_HA_ScaleSend")  
  
## <a name="high-availability-for-sending-hosts"></a>傳送主控件的高可用性  
 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的傳送功能與處理功能相似，因為這些活動都不需要主控件與資料之間的關聯。 就如同任何處理主控件執行個體都可以從 MessageBox 資料庫擷取訊息並處理它們，任何傳送主控件執行個體也可以從 MessageBox 資料庫擷取訊息並傳送它們。 因此，為傳送主控件提供高可用性表示您可以使用相同的技術為處理主控件提供高可用性。  
  
## <a name="scaling-the-biztalk-server-send-adapters"></a>擴充 BizTalk Server 傳送配接器  
  
### <a name="high-availability-for-the-msmq-send-adapter"></a>MSMQ 傳送配接器的高可用性  
 若要為 MSMQ 傳送配接器提供高可用性，您應該叢集 MSMQ 服務、在與叢集 MSMQ 服務相同群組中叢集 BizTalk 主控件，並設定 MSMQ 傳送處理常式以便在此叢集 BizTalk 主控件中執行。 您應執行這些動作以確保 MSMQ 配接器所初始化的交易傳送的一致性。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
### <a name="high-availability-for-the-windows-sharepoint-services-send-adapter"></a>Windows SharePoint Services 傳送配接器的高可用性  
 若要為 Windows SharePoint Services 傳送配接器提供高可用性，請將多部電腦新增至傳送主控件，並讓其中每部主控件電腦都參考相同的文件庫。 Windows SharePoint Services 配接器會藉由 SharePoint 電腦上的 BizTalk 所安裝的 Windows SharePoint Services web 服務呼叫，將訊息傳送至 SharePoint。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]此為 SharePoint 傳送配接器讓您將訊息推送到相同 HTTP URL 指向 SharePoint NLB 安裝的多個主控件執行個體上執行相同的傳送埠，請提供高可用性。  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)   
 [執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)
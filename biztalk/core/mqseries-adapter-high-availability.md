---
title: MQSeries 配接器的高可用性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, MQSeries adapters
- MQSeries adapters, availability
- MQSeries adapters, performance
- high availability, MQSeries adapters
ms.assetid: 4339b10b-b35d-47c0-b78a-c60207e06c8e
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 145577ce280595ff959596cff99fd08f334e8993
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008847"
---
# <a name="mqseries-adapter-high-availability"></a>MQSeries 配接器的高可用性
當您使用配接器時，可以使用下列方式來改善可用性：  
  
- 為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定容錯裝載環境。  
  
- 搭配 IBM WebSphere MQ 使用 Windows 叢集。  
  
  如需有關容錯移轉資訊和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[BizTalk Server 架構範例](../core/sample-biztalk-server-architectures.md)並[規劃您的平台容錯](../core/planning-your-platform-for-fault-tolerance.md)中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助。  
  
  為確保 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries 配接器能夠與 MQSAgent 元件的遠端安裝通訊，請確定您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和已安裝 IBM WebSphere MQ 的伺服器上已經啟用網路 COM+ 存取。 如需啟用網路 COM + 存取的詳細資訊，請參閱 Microsoft 知識庫文章編號 817065"How to enable network COM + access in Windows Server 2003"網址[ http://go.microsoft.com/fwlink/?LinkId=196580 ](http://go.microsoft.com/fwlink/?LinkId=196580)。  
  
  不需要針對搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MQSeries 配接器使用的 MQSAgent (MQSAgent2) COM+ 應用程式進行叢集。 若要為此元件提供高可用性，請在每個叢集節點安裝此元件。 若 COM+ 應用程式停止，則用戶端的下次呼叫將會啟動它。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MQSeries 配接器](../core/using-the-mqseries-adapter.md)
---
title: "MQSeries 配接器訊息流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MQSeries adapters, message flow
ms.assetid: aa5c8523-afd6-4181-9c11-a150857a7790
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5df8549f99d376ea518b160ac1505aaac7feb5fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-message-flow"></a>MQSeries 配接器訊息流程
來自 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦的訊息會先傳到在 Windows 上執行的 MQSeries Server。 在 Windows 上執行的 MQSeries Server 可以位於執行 BizTalk Server 的相同電腦上。 訊息透過 MQSeries Server for Windows 電腦路由到裝載於 UNIX 這類作業系統上的 MQSeries Server 主控件。 然後應用程式從 MQSeries 佇列擷取訊息。  
  
 來自應用程式的訊息會先傳到 MQSeries Server 上的 MQSeries 佇列。 MQSeries Server 將訊息轉送到 MQSeries Server for Windows 電腦。 BizTalk Server 從 MQSeries Server for Windows 電腦接收訊息，然後轉送到適當的應用程式。  
  
 MQSeries 配接器支援下列傳訊實例。  
  
|**狀況**|**說明**|  
|------------------|---------------------|  
|Receive|配接器從 MQSeries Server 接收已傳送到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息。|  
|傳送 (靜態單向連接埠)|配接器路由來自 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息。|  
|動態傳送|啟用應用程式在執行階段選取目的地位址 (URI)。|  
|動態接收|讓應用程式在執行階段選取位址 (URI)，藉由設定**MQSeries.DynamicReceive**內容屬性**是**並指定動態接收位址。|  
|Correlation|來自配接器的訊息與協調流程的特定執行個體相互關聯，可處理多個訊息類型。<br /><br /> MQSeries Server 可以使用請求-回應來建立相互關聯識別項，或是 BizTalk Server 可以建立相互關聯識別項。<br /><br /> 如需有關相互關聯集的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明」。|  
  
 如需有關在管線、協調流程和以內容為基礎的路由中使用連接埠與配接器的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 說明」。 如需配接器中使用相互關聯識別項的詳細資訊，請參閱[相互關聯訊息使用要求-回覆](../core/correlating-messages-using-request-reply.md)。  
  
 可用來篩選配接器中的標頭屬性的詳細資訊，請參閱[屬性相關的 BizTalk Server](../core/properties-related-to-biztalk-server.md)和[MQSeries 內容屬性](../core/mqseries-context-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MQSeries 配接器](../core/using-the-mqseries-adapter.md)
---
title: 訊息事件資料流 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dc56aff-c093-4c79-9cc7-f72079ee927f
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d955dbc2b50d1d9c40b54736762fcbaa2bfe536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262782"
---
# <a name="messaging-event-streams"></a>訊息事件資料流
當您的應用程式在安裝 BizTalk Server 的電腦上執行，而且您在追蹤做為 BizTalk 管線交易之部分的項目時，您就會使用訊息事件資料流 (Messaging Event Streams，MES)。 使用 EMS 可以確保您的 BAM 事件持續性會與 BizTalk 管線交易維持同步。  
  
 訊息事件資料流是所傳回的 EventStream 物件的執行個體[Microsoft.BizTalk.Component.Interop.IPipelineContext.GetEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.ipipelinecontext.geteventstream.aspx)方法。  
  
 訊息事件資料流是非同步的，而且會先將追蹤資料存放在 BizTalk MessageBox 資料庫中。 然後再由 Tracking Data Decode Service (TDDS) 定期處理資料，並將資料保存到 BAM 主要匯入資料庫中。  
  
 IPipelineContext 位於[Microsoft.BizTalk.Component.Interop](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx)命名空間。 若要使用 API，您必須將 Microsoft.BizTalk.Pipeline (在 microsoft.biztalk.pipeline.dll 中) 新增到您的專案中。  
  
## <a name="see-also"></a>另請參閱  
 [OrchestrationEventStream](../core/orchestrationeventstream.md)   
 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx)   
 [Microsoft.BizTalk.Component.Interop](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx)
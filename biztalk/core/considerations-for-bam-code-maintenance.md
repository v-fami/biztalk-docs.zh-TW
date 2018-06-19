---
title: BAM 的考量，程式碼維護 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, code maintenance
- BAMInterceptor class
ms.assetid: e1f1d8e0-207c-47e1-b9bd-a473c86922ce
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f7cfdb75a32c23ef5c8dedec3b6a4c783bf089a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238094"
---
# <a name="considerations-for-bam-code-maintenance"></a>BAM 程式碼維護的考量
在決定如何檢測應用程式以便使用 BAM 時，您應該考量未來需求變更的可能性。 如果您在其中一個 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) 類別上呼叫方法來寫入受監視的資料，您基本上就是以「硬式編碼」的方式在應用程式中寫入觀察模型。 如果您需要變更受監視的資料，就必須先讓應用程式離線，變更程式碼並重新編譯該應用程式，然後重新部署更新的應用程式。  
  
 或者，您可以在 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) 類別上呼叫方法，檢測您的應用程式。 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) 類別會參考組態檔來判斷要監視的事件及資料。 藉由使用 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) 類別，您可以檢測程式碼一次，然後藉由更新中繼資料來變更受監視的資料，而不需要將應用程式離線。  
  
## <a name="instrumenting-your-application-by-using-the-eventstream-object"></a>使用 EventStream 物件來檢測應用程式  
 當您要建置具有特定已知監視需求的專用應用程式時，這個方法比較簡單並且很適用。 在決定使用這個方法之前，您需要知道下列問題的答案：  
  
-   何謂 BAM 里程碑，以及在程式碼中執行其發生？  
  
-   要監視什麼資料？這些資料出現在程式碼中的時間和位置為何？  
  
 如果這些問題有任一答案可能會變更，您應該考慮改用 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx)物件來檢測應用程式。  
  
 依照這個「硬式編碼」方法進行時，您只要根據需要，在 [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx)、 [Microsoft.BizTalk.Bam.EventObservation.BufferedEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.bufferedeventstream.aspx)、 **MessagingEventStream** (在管線實作中) 或 **OrchestrationEventStream** (在協調流程實作中) 類別上呼叫方法即可。  
  
## <a name="instrumenting-your-application-by-using-the-baminterceptor-object"></a>使用 BAMInterceptor 物件來檢測應用程式  
 在下列情況中使用這個方法，效果較佳：  
  
-   您需要平衡資料的可見性與應用程式的效能，並且想要控制在執行階段監視的資料。  
  
-   應用程式會處理大量的 XML 訊息，因此，任何資料都可能變成用於監視的重要資料。  
  
-   不接受停止應用程式再將程式碼變更成監視不同的資料。  
  
 在這個方法中，您會藉由使用 [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx)類別的方法，以一般方式檢測應用程式。 藉由傳遞不同的組態到攔截器，您就可以變更 BAM 監視的資料。  
  
 您可以使用「追蹤設定檔編輯器」(TPE)，變更 BAM 從 BizTalk 協調流程收集的資料。  
  
## <a name="see-also"></a>另請參閱  
 [使用活動](../core/using-an-activity.md)   
 [何謂 BAM 攔截器？](../core/what-is-the-bam-interceptor.md)   
 [BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md)
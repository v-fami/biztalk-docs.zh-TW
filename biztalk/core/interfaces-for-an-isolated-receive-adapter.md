---
title: 介面外掛式接收配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5c6b195e-76bf-4c3e-a324-5513bc24fed1
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 129a0d16100ed7f38f49d0cfa5cc329446c3e72e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997183"
---
# <a name="interfaces-for-an-isolated-receive-adapter"></a>外掛式接收配接器介面
外掛式接收配接器是裝載於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序之外的程序空間內。 若要與「傳訊引擎」互動，外掛式接收配接器會在啟動時進行註冊，讓引擎能對它進行設定和控制。 配接器會建立傳輸 proxy，請查詢**IBTTransportProxy**，並呼叫**IBTTransportProxy.RegisterIsolatedReceiver**註冊其**IBTTransportConfig**與傳訊引擎的回呼介面。 此同步呼叫發生後，配接器才會提交其第一個訊息至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 這可讓傳訊引擎回呼配接器，告訴它哪些結束點作用中並應接聽是否有內送訊息。 外掛式配接器必須實作下列介面：  
  
- **IBTTransport**  
  
- **IBTTransportConfig**  
  
- **IBaseComponent**  
  
- **IPersistPropertyBag**  
  
  若要註冊配接器，配接器必須傳遞已設定和啟用的接收位置。 此配接器的主控件處理序必須是 BizTalk 外掛式主控件使用者群組的成員。 此外，也會查詢此配接器，確定它有正確類別識別碼，而且正在已針對該主控件執行個體設定的電腦上執行。  
  
  配接器已成功向傳輸 proxy 之後，傳訊引擎會將組態資訊傳遞和其他接收位置傳回至配接器藉由呼叫**負載**方法**IPersistPropertyBag**介面和**AddReceiveEndpoint**方法**IBTTransportConfig**分別介面。  
  
  當外掛式接收配接器結束訊息的處理，並即將終止時，它必須呼叫**TerminateIsolatedReceiver**方法**IBTTransportProxy**介面。  
  
  下圖顯示在建立外掛式接收配接器時所牽涉的物件互動。  
  
  ![](../core/media/ebiz-sdk-devadapter9.gif "ebiz_sdk_devadapter9")  
  初始化外掛式接收配接器的工作流程。  
  
> [!NOTE]
>  建議配接器應持續追蹤目前對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行中的要求。 此配接器應該封鎖**Terminate**工作計數達到零以前的方法。 在接收端，此工作包含尚未發佈至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的任何未完成要求。 請注意，回應訊息一般不會傳遞至接收配接器之後**Terminate**呼叫。 一般情況下，配接器呼叫之後**Terminate**方法中，「 傳訊引擎不接受發佈新訊息，但請求-回應組的回應訊息的要求。  
> 
> [!NOTE]
>  一個程序可能裝載數個外掛式配接器執行個體，但一個程序只能裝載一個配接器。  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發接收配接器](../core/developing-a-receive-adapter.md)   
 [具現化並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [接收配接器的內含式介面](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [交易式批次支援接收配接器介面](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [同步要求-回應接收配接器介面](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)
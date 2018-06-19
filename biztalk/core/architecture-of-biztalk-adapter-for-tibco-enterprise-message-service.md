---
title: BizTalk Adapter for TIBCO Enterprise Message Service 的架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transmit adapter
- one-way receive operations
- architecture
- one-way send operations
- receive adapter
ms.assetid: 304c7236-aacd-4761-8c33-e876b53e84ff
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c7bc6420efb67085e4f3a05f6daf0c5dbd2feb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230278"
---
# <a name="architecture-of-biztalk-adapter-for-tibco-enterprise-message-service"></a>BizTalk Adapter for TIBCO Enterprise Message Service 的架構
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 提供在 TIBCO EMS 系統與 BizTalk Server 之間交換即時商務資料的方法。 此配接器可讓 XML 應用程式與 TIBCO EMS 互動。  
  
 此配接器接受 XML 訊息，可讓 BizTalk 應用程式使用下列其中一種方式和 TIBCO EMS 進行通訊：  
  
-   **傳輸配接器**： 使用靜態單向傳送埠將訊息傳送至 TIBCO EMS。  
  
-   **接收配接器**： 使用靜態的單向接收埠以接收來自 TIBCO EMS 的訊息。  
  
## <a name="one-way-send-operation"></a>單向傳送作業  
 下圖顯示使用 BizTalk Adapter for TIBCO EMS 之單向傳送作業的架構。  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
## <a name="one-way-receive-operation"></a>單向接收作業  
 下圖顯示使用 BizTalk Adapter for TIBCO EMS 之單向接收作業的架構。  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a>另請參閱  
 [配接器功能](../core/adapter-features.md)   
 [規劃與架構](../core/planning-and-architecture16.md)
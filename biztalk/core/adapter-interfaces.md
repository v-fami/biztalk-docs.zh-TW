---
title: "配接器介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7398aeb-7c1c-400e-a552-d0ab39e55a0b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 717adcf5d4a706a7cc072b42b224ab0f9f8cc6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-interfaces"></a>配接器介面
在自訂配接器所實作的介面中，有三種介面是必要項目，另外兩種則是選擇性項目。  
  
## <a name="mandatory-interfaces"></a>必要的介面  
 所有配置器都必須實作下列介面。  
  
### <a name="ibasecomponent"></a>IBaseComponent  
 這個介面會詳細**名稱**，**版本**，和**描述**配接器。  
  
### <a name="ibttransport"></a>IBTTransport  
 這個介面會詳細**傳輸類型**和**ClassID**配接器。  
  
### <a name="ibtbatchcallback"></a>IBTBatchCallback  
 這個介面是回呼介面，透過此介面，配接器可針對提交給傳訊引擎的訊息批次而收到其狀態及錯誤資訊。  
  
## <a name="optional-interfaces"></a>選擇性介面  
 配接器可以依其需求，選擇是否要實作下列介面。  
  
### <a name="ipersistpropertybag"></a>IPersistPropertyBag  
 這是組態介面，處理常式組態會透過此介面而傳遞到配接器。 只有具有處理常式組態資訊的配接器，才需要使用這個介面。  
  
### <a name="ibttransportcontrol"></a>IBTTransportControl  
 這個介面會用來初始化及終止配接器。 傳輸 Proxy 會透過這個介面而傳遞給配接器。 對外掛式配接器而言，這個介面不是必要的。
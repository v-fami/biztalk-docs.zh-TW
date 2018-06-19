---
title: 接收器介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7ab77d4-705a-4b39-8c33-a7532ae6484c
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77b42530d721a6dcee52e082fe46deae9ae06405
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268326"
---
# <a name="receiver-interfaces"></a>接收器介面
除了標準的配接器介面，接收配接器必須實作**IBTTransportConfig**。 這是 BizTalk 傳訊引擎將接收位置傳遞到配接器時所使用的介面。  
  
## <a name="request-response-adapters"></a>要求-回應配接器  
 某些情況下，接收配接器可能也需要處理傳送訊息。 執行此操作的配接器通常稱為雙向配接器或「要求-回應」配接器。 若要能夠傳送訊息，接收配接器必須實作**IBTTransmitter**。  
  
 下圖顯示接收配接器實作的介面。  
  
> [!NOTE]
>  **IBTBatchTransmitter**介面不支援要求-回應配接器。  
  
 ![](../core/media/requestresponseadapters.gif "RequestResponseAdapters")
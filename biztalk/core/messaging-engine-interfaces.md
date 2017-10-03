---
title: "傳訊引擎介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14241db3-edcf-4449-9ec8-2171a14496c0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a135505240e94fb42e5810a3e7ac71d4c99c34a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messaging-engine-interfaces"></a>傳訊引擎介面
有三個公用介面，可供配接器用來與傳訊引擎進行互動。 下列章節中將說明這些介面。  
  
## <a name="ibttransportproxy"></a>IBTTransportProxy  
 配接器永遠都會使用自己的傳輸 Proxy 來和傳訊引擎互動。 傳輸 Proxy 會用於建立批次、取得訊息 Factory、向引擎註冊外掛式接收器等作業。  
  
## <a name="ibttransportbatch"></a>IBTTransportBatch  
 此介面是由傳訊引擎提供，它定義配接器可用來操作訊息批次的方法。 傳訊引擎會以非同步方式處理批次。  
  
## <a name="ibtdtccommitconfirm"></a>IBTDTCCommitConfirm  
 使用明確的 Microsoft Distributed Transaction Coordinator (MSDTC) 交易的配接器，必須使用此介面將使用此介面之交易的結果告知引擎。
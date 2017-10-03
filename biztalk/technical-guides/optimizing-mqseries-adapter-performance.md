---
title: "MQSeries 配接器效能最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a46455c-a8d2-4427-99bb-4e3c6dbd9566
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d4a2bd1f2cfa338d31fd574879d73249d74d08b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-mqseries-adapter-performance"></a>MQSeries 配接器效能最佳化
使用下列設定來提高效能，可能的話，以設定 MQSeries 配接器。  
  
## <a name="adjust-the-value-for-the-mqseries-receive-adapter-polling-threads"></a>MQSeries 接收配接器輪詢執行緒調整值  
 增加為指定的值**執行緒**中**MQSeries 傳輸屬性**時設定 MQSeries 配接器接收位置。 增加此屬性從預設值為 2 到 5 的值將會大幅改善的訊息可以接收使用 MQSeries 配接器的速率。  
  
## <a name="disable-transaction-support-on-mqseries-receive-locations-where-not-required"></a>停用交易支援 MQSeries 在接收位置在不需要  
 MQSeries 配接器的交易支援會帶來大量負擔。 如果交易支援不是一項業務需求，設定**交易支援**值**MQSeries 傳輸屬性** 對話方塊的預設值從**是**至**否**。  
  
## <a name="disable-ordered-delivery-of-messages-on-the-mqseries-adapter-when-not-required"></a>停用的訊息上 MQSeries 配接器時不需要排序的傳遞  
 啟用此屬性會強制排序的訊息傳遞，因為它們會從接收或傳送至 MQSeries 佇列，但將會影響效能。 啟用 排序的傳遞時，傳訊執行階段會使用單一執行緒，從指定的 MQSeries 佇列接收訊息。 如果排序傳遞的訊息不是一項業務需求，然後進行變更的預設值**Ordered**屬性**MQSeries 傳輸屬性**設定為對話方塊**否排序**。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 效能最佳化](../technical-guides/optimizing-biztalk-server-performance.md)
---
title: 如何管理多個接收位置使用 MSMQ 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- MSMQ adapters, threads
- receive locations, multiple
- threads
- receive locations, MSMQ adapters
- receive locations, threads
- configuring [MSMQ adapters], receive locations
ms.assetid: 5b2ee043-bcc9-443b-84b0-df7f487159eb
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72438551d2ecab09b918808d43e7d7de6d600677
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253806"
---
# <a name="how-to-manage-multiple-receive-locations-using-the-msmq-adapter"></a>如何使用 MSMQ 配接器管理多個接收位置
為了要增加效能，MSMQ 配接器為多執行緒。 若您有多個接收位置，可能沒有足夠的執行緒供所有接收位置使用。 如此會使部分接收位置無法提取訊息。 有三種方式可解決此問題：  
  
-   將 BizTalk 主控件新增到您的電腦，並將接收位置分配給主控件。 新增主控件可提供更多執行緒給接收位置使用。  
  
-   設定**序列處理**屬性`True`上每個接收位置。 將屬性設為 `True`，即可指派單一執行緒給各個接收位置。 如此可在集區中保留較多可用的執行緒。 但是，這樣也可能會導致效能降低。  
  
-   修改登錄以增加 MSMQ 配接器接收處理常式的主控件可用的執行緒數目。 如需詳細資訊，請參閱**修改主控件的 CLR 裝載執行緒值**區段[組態參數會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)
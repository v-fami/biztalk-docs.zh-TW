---
title: MQSeries 配接器部署選項 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, deploying
- deploying, MQSeries adapters
ms.assetid: d9380aff-40ea-419b-88e2-1e2ec3f023cb
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88fa674c38df8b31c1954234846fd3939ed8568
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263014"
---
# <a name="mqseries-adapter-deployment-options"></a>MQSeries 配接器部署選項
MQSeries 配接器讓您在設定硬體方面有很大的彈性。 至少有三種主要的使用模式：  
  
-   BizTalk Server、配接器和 MQSeries Server for Windows 都在同一部電腦上。  
  
-   BizTalk Server 和配接器在第一部電腦上，MQSeries Server for Windows (包括 MQSAgent) 在第二部電腦上，連接至執行 MQSeries Server 的一或多部其他電腦。  
  
-   群組中安裝多部 BizTalk Server 與配接器在一部電腦上，MQSeries Server (包括 MQSAgent) 安裝在另一部電腦上。  
  
-   若您將 MQSeries Server 與 MQSeries 佇列管理員叢集，配接器可以正常運作。  
  
    > [!NOTE]
    >  在此情況下，不應將 MQSAgent COM+ 應用程式叢集。 而是叢集的兩個節點應該安裝和設定 MQSAgent COM+ 應用程式。 在此狀況下，若 COM+ 應用程式停止，則用戶端的下次呼叫將會重新啟動它。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MQSeries 配接器](../core/using-the-mqseries-adapter.md)
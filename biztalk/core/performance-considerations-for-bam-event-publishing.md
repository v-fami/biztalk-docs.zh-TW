---
title: BAM 事件發佈的效能考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, BAM
- publishing, BAM
- BAM, publishing
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 5a99e61a-a3d9-47fd-a933-2297f79817a5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c031f9a3325eda9cbcf865eaf72d1d9e100616c7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997535"
---
# <a name="performance-considerations-for-bam-event-publishing"></a>BAM 事件發佈的效能考量
BAM 支援兩種發佈商務事件的型式：  
  
- 同步的  
  
- 非同步的  
  
  下圖說明這兩種模型。  
  
  ![](../core/media/bam-topologies.gif "bam_topologies")  
  BAM 拓樸  
  
  同步方式簡化了程式碼的管理與使用，非同步方式則可獲致更好的執行效能。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [同步的商務事件追蹤](../core/synchronous-business-event-tracking.md)  
  
-   [非同步的商務事件追蹤](../core/asynchronous-business-event-tracking.md)
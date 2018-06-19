---
title: BAM 攔截器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9b64ae1-4d94-4c3c-add1-fa020713be5c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 989316edff34463905c7547db815b3daaf4d4a46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230494"
---
# <a name="bam-interceptor-performance-counters"></a>BAM 攔截器效能計數器
效能計數器可以讓您針對 BAM 攔截器所執行的工作在特定方面進行監控。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下表列出 BAM 攔截器可用的效能計數器。 這些效能計數器的類別為「BAM 攔截器」。  
  
|計數器|說明|  
|-------------|-----------------|  
|Avg.失敗 BAM 事件/排清平均|在排清資料到主要匯入資料庫期間，失敗 BAM 事件的平均次數。|  
|成功 BAM 事件/排清|在資料排清到主要匯入資料庫期間，成功 BAM 事件的平均次數。 如果交易已回復，事件可能不會保存到資料庫中。|  
|Avg.擷取秒數/BAM 事件|用於擷取 BAM 事件的平均時間。|  
|Avg.排清秒數/BAM 事件|用於排清 BAM 事件的平均時間。|  
|排清期間失敗的 BAM 事件總數|在資料排清期間，失敗的 BAM 事件總數。|  
|排清期間成功的 BAM 事件總數|在排清到主要匯入資料庫期間，成功的 BAM 事件總數。 如果交易已回復，事件可能不會保存到資料庫中。|  
  
## <a name="see-also"></a>另請參閱  
 [BAM 效能計數器](../core/bam-performance-counters.md)
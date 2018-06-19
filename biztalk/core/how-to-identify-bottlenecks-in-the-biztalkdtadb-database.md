---
title: 如何識別 BizTalkDTADb 資料庫中的瓶頸 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4499bc3-d50b-4b97-b19c-93c7bcc40483
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c7463a0288733936189d3cbbb69b59b3b202419
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253758"
---
# <a name="how-to-identify-bottlenecks-in-the-biztalkdtadb-database"></a>如何識別 BizTalkDTADb 資料庫中的瓶頸
若要找出 BizTalkDTADb 資料庫中的瓶頸，請執行下列步驟：  
  
1.  確認 SQL-Agent 服務正在執行。  
  
2.  確定「封存/清除作業」服務正在執行而且即將順利完成。  
  
3.  確認是否有足夠的可用磁碟空間可以容納 DTADb 封存和資料庫成長。
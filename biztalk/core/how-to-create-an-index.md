---
title: 如何建立索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Create-Index command [BAM]
- indexes [BAM], creating
- indexes [BAM], aggregations
- creating, indexes [BAM]
- aggregations [BAM], indexes
ms.assetid: 456d94e6-2e84-4d12-ad38-49f9eeb103f3
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15fd07049ee31162b2ed69f38a99d26100e08c4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989695"
---
# <a name="how-to-create-an-index"></a>如何建立索引
系統管理員可以使用**建立索引**命令上指定之檢查點指定的活動建立索引。  
  
### <a name="to-create-an-index-on-an-activity"></a>若要建立活動的索引  
  
1. 在命令提示字元中，瀏覽至下列目錄：[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]追蹤。  
  
2. 型別**bm 建立索引-IndexName:\<的索引名稱\>-活動：\<活動名稱\>-Checkpoint:\<檢查點 1>\>**。  
  
   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
3. 按 ENTER 鍵。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM 管理公用程式](../core/bam-management-utility.md)   
 [如何刪除索引](../core/how-to-delete-an-index.md)   
 [如何取得彙總的索引清單](../core/how-to-get-a-list-of-indexes-on-an-aggregation.md)
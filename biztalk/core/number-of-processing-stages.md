---
title: 處理階段數目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 74bd9f8c-99b4-4931-a096-6c54221ab2e5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f61c5c348e54ea096c921cb6fc63f0db339dbf4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263110"
---
# <a name="number-of-processing-stages"></a>處理階段數目
解決方案將訂單程序分隔成階段，如此即可不中斷長時間執行的訂單而修改程序 (透過取代階段)。 如需如何處理程序分成兩階段的詳細資訊，請參閱 < 分割商務程序 」 中的[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。  
  
 目前版本的解決方案僅包含兩個處理階段。 不過，它可以包含更多階段。 更多的階段會提供更多的點，您可以在版本處理序，並繼續處理階段的最新版本上工作。 但是，各個階段會導致通過 MessageBox 資料庫之額外協調訊息的負擔，而增加處理時間。 您必須監控解決方案的效能，以判斷多個階段的數目是否過多。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [程序管理員邏輯](../core/process-manager-logic.md)
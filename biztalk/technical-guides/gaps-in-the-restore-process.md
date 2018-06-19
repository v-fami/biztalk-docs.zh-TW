---
title: 還原程序中的間距 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 616c4f36-8ed6-4b99-b97a-5635627dfc17
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7d3ccadd950f5a955430b982c1a6f79a262864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298094"
---
# <a name="gaps-in-the-restore-process"></a>還原程序中的間距
Master.dbo.bts_LogShippingHistory 資料表中的記錄時，您可能會注意到還原集合中的間距。 這可能有數種原因。 不過，即使在發生間斷時，才可以還原的目的系統穩定性。 間隔必須後面集，才能修復目的地環境的完整備份的還原。 如果間斷之後沒有接著還原的完整備份組，目的地環境可能會不穩定且無法還原處於一致的狀態。  
  
> [!NOTE]  
>  還原完整備份的目的只是要初步建立資料庫，並修復記錄檔歷程記錄備份鏈結中的問題。 只要還原，不會發生這個問題，完整備份組未還原，因為它們不會參與記錄備份鏈結。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解記錄傳送](../technical-guides/troubleshooting-log-shipping.md)
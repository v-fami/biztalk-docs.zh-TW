---
title: 安裝 COM + Hotfix 彙總套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 587ae3da-db65-4da8-9d3b-89effb91b197
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110dced7d3931e1987ccf966efffb700e1c5555b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020516"
---
# <a name="installing-com-hotfix-rollup-packages"></a>安裝 COM + Hotfix 彙總套件
> [!NOTE]  
>  本主題是只適用於 Windows Server 2003。  
  
 您應該安裝最新版的 Windows Server 2003 COM + hotfix 彙總套件和 Distributed Transaction Coordinator (DTC) 彙總套件的最新版本。 這是因為封裝包含許多效能和穩定性修正。  
  
 您應該執行的所有電腦上安裝這些彙總套件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和執行 SQL Server 上的所有電腦。 彙總套件是您在高輸送量的狀況下順利執行的 BizTalk 解決方案特別重要。  
  
 已修正的 DTC 問題如下所示：  
  
- 未預期的 DTC 關機  
  
- 記憶體片段相關的問題  
  
- DTC 可能會停止回應負載  
  
- DTC 可能會造成流失記憶體，或搭配使用時停止回應 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- DTC 的負載下的效能已改善  
  
## <a name="installing-the-com-rollup-package"></a>安裝 COM + 彙總套件  
 COM + 已不再發行彙總套件。 請遵循這項資訊來安裝最後一個的 COM + 封裝：  
  
-   COM + 彙總套件的最終版本是"Windows Server 2003 Post-service Pack 2 COM + 1.5 Hotfix 彙總套件 12年"。 任何版本的 Windows Server 2003，即使未安裝 service pack 會安裝此 hotfix。 此 hotfix 的詳細資訊可在 Microsoft 知識庫文件 934016， [「 可用性的 Windows Server 2003 Post-service Pack 2 COM + 1.5 Hotfix 彙總套件 12年"](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756)。  
  
## <a name="installing-the-dtc-rollup-package"></a>安裝 DTC 的彙總套件  
 DTC 會發行為獨立的 COM + 的彙總套件。 請遵循這項資訊來安裝最新的 DTC 套件：  
  
-   撰寫本文時為最新的 DTC hotfix 彙總套件會是 「 套件 16 」。 此 hotfix 的詳細資訊可在 Microsoft 知識庫文件 958013， [「 Windows Server 2003 MS DTC Hotfix 彙總套件 16 中所修正的 MS DTC 問題清單 」](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919)。  
  
     搜尋，即可找到有關最新的 DTC hotfix 彙總套件知識庫文章[ http://support.microsoft.com ](http://support.microsoft.com/)片語 （包括引號）：  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     下列查詢會為您的這項搜尋。 選擇最新的密碼：  
  
     [http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package"](http://support.microsoft.com/search/default.aspx?query=%22MS+DTC+Hotfix+Rollup+Package%22)
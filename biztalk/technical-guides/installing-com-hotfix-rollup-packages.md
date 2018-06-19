---
title: 安裝 COM + Hotfix 彙總套件 |Microsoft 文件
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
ms.openlocfilehash: 40610c649e00993323adedf0ea29330dd289a0e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298406"
---
# <a name="installing-com-hotfix-rollup-packages"></a>安裝 COM + Hotfix 彙總套件
> [!NOTE]  
>  本主題是只適用於 Windows Server 2003。  
  
 您應該安裝最新版的 Windows Server 2003 COM + hotfix 彙總套件和最新版本的分散式交易協調器 (DTC) 的彙總套件。 這是因為封裝包含許多效能和穩定性的修正。  
  
 您應該執行的所有電腦上安裝這些彙總套件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和執行 SQL Server 上的所有電腦。 彙總套件是特別重要的 BizTalk 方案中，以便在高輸送量的狀況下順利執行。  
  
 已修正的 DTC 問題如下所示：  
  
-   非預期的 DTC 關機  
  
-   記憶體分散問題  
  
-   DTC 可能會停止回應負載  
  
-   DTC 可能會造成流失記憶體，或搭配使用時停止回應[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   在負載下的 DTC 效能已改善  
  
## <a name="installing-the-com-rollup-package"></a>安裝 COM + 彙總套件  
 COM + 已不再發行彙總套件。 請遵循此資訊來安裝的最後一個 COM + 套件：  
  
-   COM + 彙總套件的最後一個版本是"Windows Server 2003 後的服務組件 2 COM + 1.5 Hotfix 彙總套件 12年"。 此 hotfix 將安裝在任何版本的 Windows Server 2003，即使未安裝 service pack。 可以找到此 hotfix 的詳細資訊，在 Microsoft 知識庫文章 934016， ["可用性的 Windows Server 2003 後的服務組件 2 COM + 1.5 Hotfix 彙總套件 12年"](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756)。  
  
## <a name="installing-the-dtc-rollup-package"></a>安裝 DTC 的彙總套件  
 將會釋出 DTC 獨立的 COM + 彙總套件。 請遵循此資訊來安裝最新的 DTC 封裝：  
  
-   撰寫本文時，最新的 DTC hotfix 彙總套件會是 [封裝 16]。 可以找到此 hotfix 的詳細資訊，在 Microsoft 知識庫文章 958013，[的清單固定的 Windows Server 2003 MS DTC Hotfix 彙總套件 16 的 MS DTC 問題 」](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919).  
  
     可以找到有關最新的 DTC hotfix 彙總套件知識庫文件，藉由搜尋[http://support.microsoft.com](http://support.microsoft.com/)片語 （包括引號）：  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     下列查詢會為您此搜尋。 選擇最新的密碼：  
  
     [http://support.microsoft.com/search/default.aspx?query= [MS + DTC + Hotfix + 彙總套件 + 封裝]](http://support.microsoft.com/search/default.aspx?query=%22MS+DTC+Hotfix+Rollup+Package%22)
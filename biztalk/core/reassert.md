---
title: "重新判斷提示 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Assert function [Business Rules Engine]
ms.assetid: 9cd640a2-bfeb-4c7a-b737-1c92cc122a9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22fcc8be7760d85a12cb05c53137177703c0fa73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="reassert"></a>重新判斷提示
若要*重新判斷提示*表示呼叫**Assert**函式在引擎中的物件上的工作記憶體。 重新判斷提示命令相當於對物件發出撤回命令，之後跟隨判斷指示命令。  
  
## <a name="net-objects"></a>.NET 物件  
 此物件是第一個被撤回的物件，而且使用此物件 (在述詞或動作中) 的規則議程上的任何動作都會被移除。 然後該物件會判斷提示回工作記憶體中，並評估為新判斷提示的任何物件。 這表示在述詞中使用此物件的任何規則都會重新評估，而且會依適當的情況將其動作新增到議程中。 之前評估為任何規則**true**並使用其動作中的物件會將其重新加入到議程的動作。  
  
## <a name="typedxmldocument"></a>TypedXmlDocument  
 當最上層**TypedXmlDocument** (**TXD**) 重新判斷提示，子**TXD**之時，會建立最上層**TXD**一開始判斷提示具有不同的行為，根據的子狀態**TXD**s。 在新的子節點或子節點已變更，這表示到至少其中一個欄位已變更的原則中使用 規則動作，判斷提示，或重新判斷提示動作上執行的子節點。 未變更的現有子節點仍存在工作記憶體中。 以下範例是一個簡化的實例，描述在重新判斷提示子節點的父節點時其子節點的行為。  
  
 假設有三個**TXD**目前在工作記憶體中的 s: **P**， **C**1， **C**2，和**C**3。 **P**是最上層**TXD**，父節點; 每個子節點都包含欄位**x**。  
  
 **P**  
  
 **C**1 (**C**1。**x** = 1)  
  
 **C**2 (**C**2。**x** = 1)  
  
 **C**3 (**C**3。**x** = 1)  
  
 接著，假設下列作業已做為規則動作的結果執行：  
  
-   欄位 (**x**) 值**C**2 更新。  
  
-   **C**3 會刪除使用使用者程式碼。  
  
-   如果是其他子節點， **D**，加入至**P**使用使用者程式碼。  
  
> [!NOTE]
>  作業的「商務規則引擎」不會將節點標示為已變更，因為引擎不處理這些動作。 例如，在外部應用程式中以程式設計方式新增、刪除或修改節點。  
  
 工作記憶體中新的物件表示法如下：  
  
 **P**  
  
 **C**1 (**C**1。**x** = 1)  
  
 **C**2 (**C**2。**x** = *0*)  
  
 **D**  
  
 現在，重新判斷提示**P**。下列幾點摘要說明子節點的行為：  
  
-   節點**C**2 已重新判斷提示，因為它已經變更正在更新其欄位之後。  
  
-   節點**C**3 會從工作記憶體撤回。  
  
-   節點**D**判斷提示至工作記憶體。  
  
-   節點**C**1 中維持不變的工作記憶體，因為它未更新之前**P**重新判斷提示。  
  
## <a name="typeddatatable"></a>TypedDataTable  
 如果**重新判斷提示**上發出**TypedDataRow**，該資料列會先撤回，然後再重新判斷提示至工作記憶體。 如果**重新判斷提示**上發出**TypedDataTable**，所有關聯**TypedDataRow**都會撤回，然進行判斷提示。  
  
## <a name="dataconnection"></a>DataConnection  
 所有**TypedDataRow**擷取透過**DataConnection**不當所致。 使用的所有述詞**DataConnection**然後重新評估，造成**DataConnection**來重新建立相關查詢**TypedDataRow**s。  
  
## <a name="see-also"></a>另請參閱  
 [引擎控制函式](../core/engine-control-functions.md)
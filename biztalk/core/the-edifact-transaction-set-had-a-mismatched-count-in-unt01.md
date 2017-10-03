---
title: "Edifact 交易集有 UNT01 不相符的計數 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2859274-78e8-4e16-92b7-c143da6da421
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 180abe338441917afa6691400a02a42e88026052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-edifact-transaction-set-had-a-mismatched-count-in-unt01"></a>Edifact 交易集有 UNT01 不相符的計數
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EfactUnhUntCountMismatch|  
|訊息文字|Edifact 交易集有 UNT01 不相符的計數。 UNT01 為 {0}，而它應該已被 {1}。 已更正。|  
  
## <a name="explanation"></a>說明  
 這個警告表示 UNT01 欄位，也就是區段計數不符交易集中的區段數目。 UNT01 值已變更或損毀，或是新增或刪除之後發現計數區段。 傳送管線重 UNT01 欄位設為正確的區段數目，然後傳送交換。  
  
## <a name="user-action"></a>使用者動作  
 使用者不必採取任何動作。
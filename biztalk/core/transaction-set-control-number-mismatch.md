---
title: "交易集控制編號不相符 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c4b0c3f-f3be-4c2c-8719-8e40aa7122b9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efd80bac6a5c58306a8d9ca64748ddbb8cb2bc81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-control-number-mismatch"></a>交易集控制編號不相符
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TsControlNumberMismatchDescription|  
|訊息文字|交易集控制編號不相符|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於交易集 [SE02] 欄位中的控制編號和 [ST02] 欄位中的控制編號不符，因此 EDI 接收管線拒絕內送交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，讓傳送者交易集的變更，而 SE02 欄位中已拒絕的交易集，使 [ST02] 欄位中的控制編號與相同的控制編號，然後再重新傳送交換。
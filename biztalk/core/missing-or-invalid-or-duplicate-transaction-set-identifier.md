---
title: "遺漏或無效或重複的交易集識別項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8580aab2-9fa4-43fb-b643-10621926591e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75251d0210be4ed34a74ba0f3f5cadf84d9941b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="missing-or-invalid-or-duplicate-transaction-set-identifier"></a>遺漏或無效或重複的交易集識別項
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TsMissingOrInvalidTsIdentiferDescription2|  
|訊息文字|遺漏或無效或重複的交易集識別項 '{0}'|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收或傳送管線無法處理 X12 交換交易的值設定識別碼 （ST01 欄位中），因為遺漏，重複出現，或有無效的值。 如果文件結構描述沒有 ST 標頭和 SE 結尾，也可能會發生。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定交換 ST01 欄位的值而結構描述擁有的 ST 標頭和 SE 結尾的項目。 請確認的 ST01 值是有效的三位數文件類型指示項。 請確認 ST01 欄位不是重複項目與另一個交易集合的 ST01 欄位。
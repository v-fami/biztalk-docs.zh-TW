---
title: "比較只能 Equals、 NotEquals 和 Exists |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aad902a2-d0dc-4d91-87a7-a6305e2f40e0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: add062aebdbabe7d5965b46c7342595f96a7b8dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-comparison-can-only-be-equals-notequals-and-exists"></a>比較只能 Equals、 NotEquals 和 Exists
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|Err_InvalidComparision|  
|訊息文字|比較只能 Equals、 NotEquals 和 Exists。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法將內容屬性做比較來決定訊息的批次嘗試時。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請在作用中批次中提供的篩選條件不會指定不支援其他作業的 XSD 型別等於、 NotEquals 和 Exists 以外的運算子。
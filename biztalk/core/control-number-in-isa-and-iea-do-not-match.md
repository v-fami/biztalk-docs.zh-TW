---
title: ISA 和 IEA 中的控制編號不相符 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f9091ea-460b-464b-acd5-8dc0488b61e5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd2f86d767b6065a6aeaa02f887dc8b6bd056fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237902"
---
# <a name="control-number-in-isa-and-iea-do-not-match"></a>ISA 和 IEA 中的控制編號不相符
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|ISA 和 IEA 中的控制編號不相符|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於包含在內送交換之 [ISA13] 和 [IEA02] 欄位中的交換控制編號值不同，因此 AS2 接收管線無法處理該交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 ISA13] 和 [IEA02 交換的欄位中包含的交換控制編號具有相同的值，並接著必須重新傳送交換。
---
title: "此 AS2 交換的合作對象 AS2 必須包含值-從 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d338759-5646-4dc2-8319-a42aaa8c3d9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b52f153cce06eac014d98fa1908978694fc67706
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-from"></a>此 AS2 交換的合作對象必須包含 AS2-From 的值
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|InvalidAgreementAS2FromName|  
|訊息文字|此 AS2 交換的合作對象必須包含 AS2-From 的值。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法傳送 AS2 訊息，因為 AS2-從屬性未設定已解析合作對象做為訊息接收者。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，開啟 BizTalk Server 管理主控台，移至合作對象節點中，開啟 AS2 屬性 對話方塊的 合作對象解析訊息時，按一下合作對象當做 AS2 訊息接收者節點，然後輸入 AS2 的值-屬性。
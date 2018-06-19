---
title: 此 AS2 交換的合作對象 AS2 必須包含值-至 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 029eae5d-4c13-402d-90c5-8e9ef3814a1f
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4adda90c2ae0e5dfa659e3bd36dcadfc58f815ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279086"
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-to"></a>此 AS2 交換的合作對象 AS2 必須包含值-至
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|InvalidAgreementAS2ToName|  
|訊息文字|此 AS2 交換的合作對象必須包含 AS2-To 的值。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄 AS2 訊息因為 AS2-屬性未設定已解析合作對象做為訊息接收者。 這表示外寄 AS2 訊息的合作對象已解析藉由比對訂閱訊息的傳送埠的合作對象相關聯的傳送埠。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行作業，如下所示：  
  
1.  開啟 [BizTalk Server 管理] 主控台。  
  
2.  移至 [合作對象] 節點，然後開啟 [AS2 屬性] 對話方塊的合作對象解析訊息。  
  
3.  您可以按一下 合作對象做為 AS2 訊息接收者的節點。  
  
4.  輸入 AS2 的值-屬性。
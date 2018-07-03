---
title: 此 AS2 交換的合作對象必須包含值的 AS2-以 |Microsoft Docs
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
ms.openlocfilehash: 333657b16b0e4a0b9bbbb30c73641f7db8466b87
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006695"
---
# <a name="the-party-for-this-as2-interchange-must-contain-a-value-for-as2-to"></a>此 AS2 交換的合作對象必須包含值的 AS2-到
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                               InvalidAgreementAS2ToName                                |
|  訊息文字   |          此 AS2 交換的合作對象必須包含 AS2-To 的值。           |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄 AS2 訊息因為 AS2-屬性未設定已解析合作對象做為訊息接收者。 這表示外, 寄 AS2 訊息的合作對象已解析所比對訂閱訊息的傳送埠的合作對象相關聯的傳送埠。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列步驟：  
  
1.  開啟 [BizTalk Server 管理] 主控台。  
  
2.  移至 [合作對象] 節點中，然後開啟 [AS2 屬性] 對話方塊中的合作對象解析訊息。  
  
3.  您可以按一下 合作對象做為 AS2 訊息接收者的節點。  
  
4.  輸入 AS2 的值-屬性。
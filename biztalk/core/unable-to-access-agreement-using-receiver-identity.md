---
title: 無法使用接收者識別存取協議 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 470325f4-abc4-40bb-9109-9ffc73b496df
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 630ce4850c2bb11f9b5a18db03204ef2c1e24cae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003727"
---
# <a name="unable-to-access-agreement-using-receiver-identity"></a>無法使用接收者識別存取協議
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                         UnableToLocateAS2PartyByPartyNameError                         |
|  訊息文字   |                無法使用接收者識別存取協議： {0}                 |
  
## <a name="explanation"></a>說明  
 此錯誤表示，傳送管線無法判斷外寄 AS2 訊息的合作對象因為它無法符合外寄訊息的 AS2To 內容屬性或 Http.UserHttpHeaders 內容屬性的名稱中的 AS2To 屬性合作對象的 as2-合作對象當做 AS2 訊息接收者頁面的 [AS2 屬性] 對話方塊中的屬性。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請設定 AS2-的合作對象當做 AS2 訊息接收者頁面錯誤的 AS2 訊息相關聯的適當的合作對象名稱的 AS2 屬性 對話方塊中的屬性。
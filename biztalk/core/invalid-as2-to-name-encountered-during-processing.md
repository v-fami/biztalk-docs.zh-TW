---
title: 無效的 AS2-處理過程中發現名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84d848b5-b2a3-460d-85d4-c3576e4e3aaf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32ba8039d57bdc88f2aeed8e2654c5dc738f3d69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002671"
---
# <a name="invalid-as2-to-name-encountered-during-processing"></a>無效的 AS2-在處理期間發生的名稱
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                            InvalidAS2ToNameEncounteredError                            |
|  訊息文字   |             無效的 AS2-在處理期間發生的名稱。  值： {0}             |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換或傳送管線無法處理外寄交換，因為值的 AS2-To 標頭不符合AS2 RFC 4130 中的規格。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 AS2-To 標頭中傳入或傳出的訊息符合 AS2 RFC 4130 第 6.2 節的規格。
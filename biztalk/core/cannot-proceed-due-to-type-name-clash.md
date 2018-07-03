---
title: 無法繼續，因為類型名稱衝突 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ced6de4-0950-498e-a548-5c85419726d8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 742d537f2329c53cd974abbaac9a6b9f7f8f5126
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008479"
---
# <a name="cannot-proceed-due-to-type-name-clash"></a>無法繼續，因為類型名稱衝突
## <a name="details"></a>詳細資料  
  
|                 |                                                                                       |
|-----------------|---------------------------------------------------------------------------------------|
|  產品名稱   |  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |              [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]               |
|    事件識別碼     |                                           0                                           |
|  事件來源   |                                           0                                           |
|    元件    |                                           0                                           |
|  符號名稱  |                                           0                                           |
|  訊息文字   | 無法繼續，因為類型名稱衝突。 名稱"{0}"已經存在於的命名空間 |
  
## <a name="explanation"></a>說明  
 此錯誤表示在同一個定義的命名空間中的多個成品具有相同的名稱。  
  
## <a name="user-action"></a>使用者動作  
 重新命名相同的命名空間中的成品，或將它們放在不同的命名空間。
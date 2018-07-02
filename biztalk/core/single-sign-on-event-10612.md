---
title: 單一登入： 事件 10612 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9d9e6f5-06b8-4989-a0dc-6e2e5980443b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fdc86dd2143bf8b2b4c27dab66cc4c06ddff5ae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973015"
---
# <a name="single-sign-on-event-10612"></a>單一登入： 事件 10612
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                 |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                            企業單一登入                                                                                                                            |
| 產品版本 |                                                                                                           [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                            |
|    事件識別碼     |                                                                                                                                      10612                                                                                                                                      |
|  事件來源   |                                                                                                                                     ENTSSO                                                                                                                                      |
|    元件    |                                                                                                                                       不適用                                                                                                                                       |
|  符號名稱  |                                                                                                                          SSO_WARN_TRANSACTION_TIMEOUT                                                                                                                           |
|  訊息文字   | 交易逾時超過建議的最大，這項作業。 請參閱 details.%r 文件<br /><br /> 交易識別碼: %1 %r<br /><br /> 交易逾時: （輸入 0 表示無限逾時） 的 %2 分鐘 %r<br /><br /> 最大建議的值： %3 分鐘 |
  
## <a name="explanation"></a>說明  
 交易已進入系統的非常大型的逾時值。 如果鎖定長時間執行交易時，ENTSSO 系統就會輪詢 SSO 資料庫，系統會最後變成離線。  
  
## <a name="user-action"></a>使用者動作  
 使用者不必採取任何動作。
---
title: 單一登入： 事件 10614 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1f9cd21-3f4b-446f-a4c7-15266973adf1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba6cae7c64b5eeff339499f279aa85917211cbba
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968167"
---
# <a name="single-sign-on-event-10614"></a>單一登入： 事件 10614
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                         |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                        企業單一登入                                                                                                        |
| 產品版本 |                                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                        |
|    事件識別碼     |                                                                                                                  10614                                                                                                                  |
|  事件來源   |                                                                                                                 ENTSSO                                                                                                                  |
|    元件    |                                                                                                                   不適用                                                                                                                   |
|  符號名稱  |                                                                                                     SSO_WARN_INVALID_TICKET_TIMEOUT                                                                                                     |
|  訊息文字   | 票證逾時值對於全域資訊更新無效。%r<br /><br /> 票證逾時： %1 分鐘 %r<br /><br /> 最小票證逾時： 1 分鐘 %r<br /><br /> 最大票證逾時： %2 分鐘 %r<br /><br /> 錯誤碼： %3 |
  
## <a name="explanation"></a>說明  
 指定票證逾時值無效。  
  
## <a name="user-action"></a>使用者動作  
 您可以使用所提供的警告訊息中的資訊來修正值。
---
title: 單一登入： 事件 10585 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51c55ada-1ee3-4626-b044-9c537d11f0d9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a423ae8ca3328b2e3846c953036ae70aa6ff4f05
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966831"
---
# <a name="single-sign-on-event-10585"></a>單一登入： 事件 10585
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                           |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                 企業單一登入                                                                                 |
| 產品版本 |                                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                 |
|    事件識別碼     |                                                                                           10585                                                                                           |
|  事件來源   |                                                                                          ENTSSO                                                                                           |
|    元件    |                                                                                            不適用                                                                                            |
|  符號名稱  |                                                                             SSO_WARN_EXPIRED_TICKET_REDEEMED                                                                              |
|  訊息文字   | 票證逾時期限過期後，就會贖回票證。 這是允許的，因為已停用此應用程式的票證逾時。%r<br /><br /> 應用程式名稱： %1 |
  
## <a name="explanation"></a>說明  
 票證逾時可啟用或停用。 在此案例中，即使票證逾時期限過期也會贖回票證，因為逾時已停用。  
  
## <a name="user-action"></a>使用者動作  
 如果逾時為停用，則使用者不必採取任何動作。 但是，如果您不知道此特定應用程式已停用其逾時，請立即檢查應用程式以確定您要允許停用。
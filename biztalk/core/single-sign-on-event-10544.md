---
title: 單一登入： 事件 10544 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c79e2186-1c75-4e7b-8bf5-f582e5c2aac7
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f476e664d50d05a57f42006ec08aa03d901e9f1f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983927"
---
# <a name="single-sign-on-event-10544"></a>單一登入： 事件 10544
## <a name="details"></a>詳細資料  

|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10544                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                             CO                             |
|  符號名稱  |                  SSO_WARN_TICKET_EXPIRED                   |
|  訊息文字   | 票證已過期。%r<br /><br /> 應用程式名稱： %1 |

## <a name="explanation"></a>說明  
 這個警告事件表示應用程式票證逾時已過期。 您可以在系統層級和應用程式層級指定票證逾時。 如果已指定系統層級和應用程式層級的逾時，應用程式層級的逾時用來決定到期時間。  

## <a name="user-action"></a>使用者動作  
 若要解決這個警告，請執行下列一或多個動作：  

- 決定票證到期之前要驗證的原因。  

- 確保票證逾時值是足以上次之間贖回時間發出票證的時間。  

  如需詳細資訊，請參閱中的下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  

- [SSO 票證](../core/sso-tickets.md)  

- [如何設定 SSO 票證](../core/how-to-configure-the-sso-tickets.md)

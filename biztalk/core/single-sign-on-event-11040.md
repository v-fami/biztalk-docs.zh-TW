---
title: 單一登入： 事件 11040 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e6ccdc06-9677-4454-ae2c-8dde78d6f3f8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eefc6c65e07b430851606ce7779aad3771776a83
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019068"
---
# <a name="single-sign-on-event-11040"></a>單一登入： 事件 11040
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                             |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                  企業單一登入                                                                  |
| 產品版本 |                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                  |
|    事件識別碼     |                                                                            11040                                                                            |
|  事件來源   |                                                                           ENTSSO                                                                            |
|    元件    |                                                                             不適用                                                                             |
|  符號名稱  |                                                                  SSO_WARN_NETWORK_SERVICE                                                                   |
|  訊息文字   | SSO 服務正在網路服務帳戶下執行。 這個帳戶有一些特殊考量。 請參閱 details.%r 您文件 |
  
## <a name="explanation"></a>說明  
 SSO 服務正在網路服務帳戶下執行。 這個帳戶有一些特殊考量。 例如，新增網路服務帳戶之後需要重新開機。 而且，在網路服務帳戶下執行會限制您在相當有限的情況下執行。  
  
## <a name="user-action"></a>使用者動作  
 如需詳細資訊，請參閱 < [SSO 安全性建議](../core/sso-security-recommendations.md)。
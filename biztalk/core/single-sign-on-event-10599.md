---
title: 單一登入： 事件 10599 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd671aa5-b243-4081-9a4e-87103be9a1d7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 326b94be9c05be6645a21b10f3ea302cf63be8e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015679"
---
# <a name="single-sign-on-event-10599"></a>單一登入： 事件 10599
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                    |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                             企業單一登入                                                                              |
| 產品版本 |                                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                             |
|    事件識別碼     |                                                                                       10599                                                                                        |
|  事件來源   |                                                                                       ENTSSO                                                                                       |
|    元件    |                                                                                        不適用                                                                                         |
|  符號名稱  |                                                                              SSO_WARN_ENTSSO_IS_ADMIN                                                                              |
|  訊息文字   | SSO 服務正在本機系統管理員帳戶下執行。 基於安全理由，並不建議使用這個做法。 請參閱 details.%r 文件<br /><br /> SSO 服務帳戶： %1 |
  
## <a name="explanation"></a>說明  
 指定的 SSO 服務正在本機系統管理員帳戶下執行的。 基於安全理由，並不建議使用這個做法。  
  
## <a name="user-action"></a>使用者動作  
 如需詳細資訊，請參閱 < [SSO 安全性建議](../core/sso-security-recommendations.md)。
---
title: 單一登入： 事件 10550 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73d63bc5-1e60-426c-a0d6-55c51dbb8d76
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 987e01d741ef49245c931f828f6cebeb3bf52cd2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021956"
---
# <a name="single-sign-on-event-10550"></a>單一登入： 事件 10550
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                           企業單一登入                                                                                           |
| 產品版本 |                                                                          [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                           |
|    事件識別碼     |                                                                                                     10550                                                                                                     |
|  事件來源   |                                                                                                    ENTSSO                                                                                                     |
|    元件    |                                                                                                      不適用                                                                                                      |
|  符號名稱  |                                                                                        SSO_ERROR_SERVICE_NOT_SSO_ADMIN                                                                                        |
|  訊息文字   | SSO 服務無法啟動，因為它執行的服務帳戶不是 SSO 系統管理員 account.%r 的成員<br /><br /> SSO 系統管理員: %1 %r<br /><br /> SSO 服務帳戶： %2 |
  
## <a name="explanation"></a>說明  
 SSO 服務必須執行的服務帳戶是 SSO 系統管理員帳戶的成員。  
  
## <a name="user-action"></a>使用者動作  
 如需詳細資訊，請參閱 <<c0> [ 如何指定 SSO 系統管理員和分支機構系統管理員帳戶](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md)。
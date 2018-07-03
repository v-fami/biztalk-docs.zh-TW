---
title: 單一登入： 事件 11060 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4851fba-0d3a-4a29-b720-a1d175d20555
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74fd521f2b2dab27a3a408e8459d5bb4113252d7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022732"
---
# <a name="single-sign-on-event-11060"></a>單一登入： 事件 11060
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                               企業單一登入                                                                                               |
| 產品版本 |                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                               |
|    事件識別碼     |                                                                                                         11060                                                                                                         |
|  事件來源   |                                                                                                        ENTSSO                                                                                                         |
|    元件    |                                                                                                          不適用                                                                                                          |
|  符號名稱  |                                                                                            SSO_WARN_PS_MIIS_ACCESS_DENIED                                                                                             |
|  訊息文字   | 來自 MIIS 的 Windows 密碼變更將只接受從 SSO 服務 account.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> SSO 服務帳戶: %3 %r<br /><br /> 錯誤碼： %4 |
  
## <a name="explanation"></a>說明  
 ENTSSO 伺服器從 Microsoft Identity Integration Server (MIIS) 收到密碼變更。 不過，ENTSSO 伺服器將只會接受來自 MIIS 的密碼變更，如果用戶端使用者 （呼叫者） 是做為 SSO 服務帳戶相同的帳戶。  
  
## <a name="user-action"></a>使用者動作  
 請檢查在 MIIS 的密碼同步處理的呼叫端的組態。 如需詳細資訊，請參閱 <<c0> [ 如何以進行 MIIS 密碼同步設定的 ENTSSO](../core/how-to-configure-entsso-for-miis-password-sync.md)。
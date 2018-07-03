---
title: 單一登入： 事件 11025 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df5a733b-3c95-409c-8485-bf3f7feb3c50
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd8c25dc80669b4524c7e9ce848e4b0e28f773f4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015895"
---
# <a name="single-sign-on-event-11025"></a>單一登入： 事件 11025
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                            |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                 企業單一登入                                                                                                  |
| 產品版本 |                                                                                 [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                 |
|    事件識別碼     |                                                                                                           11025                                                                                                            |
|  事件來源   |                                                                                                           ENTSSO                                                                                                           |
|    元件    |                                                                                                            不適用                                                                                                             |
|  符號名稱  |                                                                                            SSO_WARN_INVALID_APP_TICKET_TIMEOUT                                                                                             |
|  訊息文字   | 對應用程式 update.%r 的票證逾時值無效<br /><br /> 應用程式名稱: %1 %r<br /><br /> 票證逾時： %2 分鐘 %r<br /><br /> 最大票證逾時： %3 分鐘 %r<br /><br /> 錯誤碼： %4 |
  
## <a name="explanation"></a>說明  
 票證逾時值無效。  
  
## <a name="user-action"></a>使用者動作  
 如需有關票證逾時的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。
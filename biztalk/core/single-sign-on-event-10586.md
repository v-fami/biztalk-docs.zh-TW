---
title: 單一登入： 事件 10586 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7d480e9-dc34-44ac-9272-0caf80237bd9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b353c5d9fb569da7bcc35927e31ce5c3e68ae11
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978869"
---
# <a name="single-sign-on-event-10586"></a>單一登入： 事件 10586
## <a name="details"></a>詳細資料  
  
|                 |                                                             |
|-----------------|-------------------------------------------------------------|
|  產品名稱   |                  企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]  |
|    事件識別碼     |                            10586                            |
|  事件來源   |                           ENTSSO                            |
|    元件    |                             不適用                             |
|  符號名稱  |                   SSO_WARN_CRED_CACHE_OFF                   |
|  訊息文字   | 已停用這部 SSO 伺服器的認證快取。 |
  
## <a name="explanation"></a>說明  
 認證快取，通常會啟用，已停用。 只有系統管理員可以啟用或停用認證快取。 停用認證快取將有時可能會導致較新的認證，從 ENTSSO 系統中，雖然它會降低效能。  
  
## <a name="user-action"></a>使用者動作  
 若要重新啟用認證快取，請參閱 Afflilate 應用程式屬性的表格[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。
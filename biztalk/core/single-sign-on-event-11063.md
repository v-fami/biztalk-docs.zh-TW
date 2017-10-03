---
title: "單一登入： 事件 11063 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c84f91de-221d-43c4-8d23-3d1b7fd29cf7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82581dafd58a07ed217a5e9062aa91057a84aed3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11063"></a>單一登入： 事件 11063
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11063|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_PS_MIIS_CALLBACK_ACCESS_DENIED|  
|訊息文字|密碼同步伺服器 (針對 MIIS) 存取遭拒。%r|  
  
## <a name="explanation"></a>說明  
 MIIS 回呼存取被拒。 此錯誤最可能的原因是未使用的 MIIS 和 ENTSSO 系統之間的 Kerberos 驗證。  
  
## <a name="user-action"></a>使用者動作  
 確認 ENTSSO 系統使用 Kerberos 驗證。 如需詳細資訊，請參閱[SSO 安全性建議](../core/sso-security-recommendations.md)。
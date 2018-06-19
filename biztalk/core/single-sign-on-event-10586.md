---
title: 單一登入： 事件 10586 |Microsoft 文件
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
ms.openlocfilehash: 124ed0a722d0da0f21722f3b337c8bb938068b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270710"
---
# <a name="single-sign-on-event-10586"></a>單一登入： 事件 10586
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10586|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_CRED_CACHE_OFF|  
|訊息文字|已停用這部 SSO 伺服器的認證快取。|  
  
## <a name="explanation"></a>說明  
 認證快取，通常會啟用，已停用。 只有系統管理員可以啟用或停用認證快取。 停用認證快取有時會比較目前的認證從 ENTSSO 系統中，雖然會降低效能。  
  
## <a name="user-action"></a>使用者動作  
 若要重新啟用認證快取，請參閱 Afflilate 應用程式屬性的表格[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。
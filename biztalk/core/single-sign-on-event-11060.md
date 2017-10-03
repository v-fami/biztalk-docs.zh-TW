---
title: "單一登入： 事件 11060 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4851fba-0d3a-4a29-b720-a1d175d20555
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1423b7385e6c0b8f78fb815ec48b749556cd291f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11060"></a>單一登入： 事件 11060
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11060|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_PS_MIIS_ACCESS_DENIED|  
|訊息文字|來自 MIIS 的 Windows 密碼變更只能從 SSO 服務 account.%r 接受<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者: %2 %r<br /><br /> SSO 服務帳戶: %3 %r<br /><br /> 錯誤碼： %4|  
  
## <a name="explanation"></a>說明  
 已由 ENTSSO 伺服器從 Microsoft Identity Integration Server (MIIS) 接收密碼變更。 不過，如果用戶端使用者 （呼叫端） 是做為 SSO 服務帳戶的相同帳戶 ENTSSO 伺服器將只接受來自 MIIS 的密碼變更。  
  
## <a name="user-action"></a>使用者動作  
 檢查呼叫端的 MIIS 的密碼同步處理的設定。 如需詳細資訊，請參閱[如何設定 ENTSSO 進行 MIIS 密碼同步](../core/how-to-configure-entsso-for-miis-password-sync.md)。
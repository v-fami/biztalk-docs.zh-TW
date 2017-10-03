---
title: "單一登入： 事件 11068 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f09a1191-ae67-4156-a8a5-d24e4439fc68
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be824a9205d81aaaeb9fd87129133b94b4f2e379
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11068"></a>單一登入： 事件 11068
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11068|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_LOOKUP_CALLBACK_ACCESS_DENIED_NO_REMOTE|  
|訊息文字|拒絕存取尋查伺服器。 這部 SSO 伺服器目前未設定為允許遠端尋查。 使用 'ssoconfig-remote 尋查 yes' 或 SSO 管理 MMC.%r|  
  
## <a name="explanation"></a>說明  
 存取查閱伺服器被拒因為 ENTSSO 伺服器並未設定為允許遠端尋查。  
  
## <a name="user-action"></a>使用者動作  
 若要允許遠端尋查，**伺服器嵌入式管理單元**，**進階**索引標籤上，選取**允許遠端尋查**。  
  
 如需詳細資訊，請參閱[如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。
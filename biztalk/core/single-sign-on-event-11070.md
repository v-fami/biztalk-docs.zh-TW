---
title: "單一登入： 事件 11070 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb669df9-710a-4792-bdd4-cca0c03fcda2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb0d2a868d5c8bf47cbcb5389bf2d16dadf4010a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11070"></a>單一登入： 事件 11070
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11070|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_PS_MIIS_NOT_ALLOWED|  
|訊息文字|這部 SSO 伺服器目前未設定為允許來自 MIIS 的 Windows 密碼變更。 使用 'ssoconfig-allowPS MIIS yes' 或 SSO 管理 MMC.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 用戶端使用者： %2|  
  
## <a name="explanation"></a>說明  
 這部 SSO 伺服器目前未設定為允許來自 MIIS 的 Windows 密碼變更。  
  
## <a name="user-action"></a>使用者動作  
 若要允許的 Windows 密碼變更從 MIIS，**伺服器嵌入式管理單元**，**密碼同步屬性**索引標籤上，選取**允許從 MIIS 進行密碼同步。**  
  
 如需詳細資訊，請參閱[如何使用伺服器嵌入式管理單元](../core/how-to-use-the-servers-snap-in.md)。
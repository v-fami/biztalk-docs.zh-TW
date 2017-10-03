---
title: "單一登 On1 需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, Single Sign-On
- SSO, requirements [JD Edwards EnterpriseOne adapters]
- adapters [JD Edwards EnterpriseOne adapters], Single Sign-On
- Single Sign-On, requirements [JD Edwards EnterpriseOne adapters]
- Single Sign-On, enabling [JD Edwards EnterpriseOne adapters]
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfab6d6cfea2ddef3b953d3fb3bb15900420fdcf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-for-single-sign-on"></a>單一登入的需求
若要使用單一登入 (SSO)，您必須已安裝下列軟體：  
  
-   Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]  
  
-   企業單一登入  
  
-   支援 SSO 的伺服器系統  
  
-   外掛式主控的件應設定為**信任的驗證**。  
  
### <a name="to-enable-sso"></a>啟用 SSO  
  
1.  在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。  
  
2.  指定傳輸屬性時，選取適當的分支機構應用程式。  
  
 如需建立分支機構應用程式的資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications4.md)。  
  
> [!NOTE]
>  執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。 如果資料夾是共用的，使用該資料夾的應用程式將不會正確更新或解除安裝，因為它會被視為使用中。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on1.md)
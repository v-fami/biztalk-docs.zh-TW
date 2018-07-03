---
title: 進行單一登入的需求 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1111377-2fe1-4d65-ac0d-c89d2f1740b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9045c51470d666906c090b55d6307c9f85d20e0c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022476"
---
# <a name="requirements-for-single-sign-on"></a>單一登入的需求
若要使用單一登入 (SSO)，您必須已安裝下列軟體：  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   企業單一登入  
  
-   支援 SSO 的伺服器系統  
  
-   外掛式主控件應設定為**信任的驗證**。  
  
## <a name="enable-sso"></a>啟用 SSO  
  
1. 在 **傳輸屬性**視窗中，選取**是**for**使用 SSO**。  
  
2. 指定傳輸屬性時，選取適當的分支機構應用程式。  
  
   如需建立分支機構應用程式的資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications4.md)。  
  
> [!NOTE]
>  執行工作之後使用 SSO，請務必重設任何 Web 共用的資料夾，以**不會共用**。 如果資料夾是共用的，使用該資料夾的應用程式將不會正確更新或解除安裝，因為它會被視為使用中。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for JD Edwards EnterpriseOne 中的安全性](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)
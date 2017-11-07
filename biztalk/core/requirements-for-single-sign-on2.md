---
title: "單一登入的需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae4b5c1f-1718-4628-9159-2fb877498913
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e0dc92e4492d36ca8204f61354f8422d7eb47631
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="requirements-for-single-sign-on"></a>單一登入的需求
若要使用「單一登入」(SSO)，您需要：  
  
-   BizTalk Server
  
-   Visual Studio  
  
-   企業單一登入  
  
-   支援 SSO 的伺服器系統  
  
 外掛式主控件應設定為信任的驗證  
  
## <a name="enable-sso"></a>啟用 SSO  
  
1.  在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。  
  
2.  指定傳輸屬性時，選取適當的分支機構應用程式。  
  
 如需如何建立分支機構應用程式資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications2.md)。  
  
> [!NOTE]
>  執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。 不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。  
  
## <a name="see-also"></a>另請參閱  
 [執行 SSO 專案](../core/running-sso-projects1.md)   
 [保護配接器](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)
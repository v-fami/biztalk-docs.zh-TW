---
title: "單一登入的需求 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d5c406b-f548-4df0-8644-fdf6a812a989
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61932b44364670515f02f89a1441a5d54030bc94
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="requirements-for-single-sign-on"></a>單一登入的需求
若要使用「單一登入」(SSO)，您必須具有下列項目：  
  
-   Microsoft BizTalk Server
  
-   Visual Studio  
  
-   企業單一登入  
  
-   支援 SSO 的伺服器系統  
  
-   外掛式主控件應設定為信任的驗證。  
  
## <a name="enable-sso"></a>啟用 SSO  
  
1.  在**傳輸屬性**視窗中，選取**是**如**使用 SSO**。  
  
2.  指定傳輸屬性時，選取適當的分支機構應用程式。  
  
 如需詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications1.md)。  
  
> [!NOTE]
>  執行工作之後使用 SSO，請記得要重設任何 Web 共用資料夾，以**不會共用**。 不使用該資料夾的應用程式將會更新，或如果資料夾共用，因為它會被視為使用中正確地解除安裝。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一登入](../core/using-single-sign-on5.md)
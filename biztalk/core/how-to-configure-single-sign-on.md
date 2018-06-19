---
title: 如何設定單一登入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 511edc1d-de82-4d17-88ea-6cacfccde10d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3203be74b21fa742e8e1ec2972e40f0212c4d1bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247766"
---
# <a name="how-to-configure-single-sign-on"></a>如何設定單一登入
在存取「企業單一登入」之前，您應該確認目前的使用者已正確設定「企業單一登入」。 對於多數組態，您會使用兩個介面的其中一個。 `ISSOAdmin`是可讓您建立新的分支機構應用程式的一般系統管理介面。 不過，藉由使用 ISSOAdmin.GetGlobalInfo 和 ISSOAdmin.UpdateGlobalInfo，您可以設定各種旗標和管理值。 如下所述的一項可能工作就是確保已經啟用 SSO 票證。  
  
### <a name="to-enable-ticketing"></a>若要啟用票證  
  
1.  建立新的 `ISSOAdmin` 執行個體。  
  
2.  透過 `ISSOAdmin.GetGlobalInfo` 擷取目前的設定。  
  
     如有需要，您可能要在此時確認旗標已設定為正確的值。  
  
3.  使用 `ISSOAdmin.UpdateGlobalInfo` 變更任何相關的旗標。  
  
     在本個案中，所有旗標均會設為驗證並啟用票證。  
  
 下列範例顯示如何使用「單一登入」啟用票證。  
  
```  
public static bool EnableTickets()  
{  
   try  
   {  
      ISSOAdmin admin=new ISSOAdmin();  
      int flags=0;  
      int appDeleteMax=1000;  
      int mappingDeleteMax=1000;  
      int ntpLookupMax=-1000;  
      int xplLookupMax=-1000;  
      int ticketTimeout=2;  
      int cacheTimeout=60;  
      string secretServer=null;  
      string ssoAdminGroup=null;  
      string affiliateAppMgrGroup=null;  
      // Get current default settings.  
      admin.GetGlobalInfo(out flags, out appDeleteMax, out mappingDeleteMax, out ntpLookupMax, out xplLookupMax, out ticketTimeout, out cacheTimeout, out secretServer, out ssoAdminGroup, out affiliateAppMgrGroup);  
      // Update global settings.  
      admin.UpdateGlobalInfo(SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, ref appDeleteMax, ref mappingDeleteMax, ref ntpLookupMax, ref xplLookupMax, ref ticketTimeout, ref cacheTimeout, null, null, null);   
   }  
   catch  
   {  
      return false;  
   }  
return true;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用企業單一登入進行程式設計](../core/programming-with-enterprise-single-sign-on.md)
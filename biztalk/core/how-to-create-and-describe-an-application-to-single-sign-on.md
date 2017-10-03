---
title: "如何建立和描述應用程式單一登入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d717885-b132-4ba0-a93b-03377ac5eb97
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 423439795d9a3822427edbee2e062c3c0aa6bb80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-and-describe-an-application-to-single-sign-on"></a>如何建立和描述應用程式單一登入
您需要執行的常見管理工作是將分支機構應用程式新增至「企業單一登入」(SSO) 資料庫。 新增分支機構應用程式到「企業 SSO」資料庫可讓您將使用者和認證與分支機構應用程式建立關聯。  
  
> [!NOTE]
>  建立分支機構應用程式需要「SSO 應用程式管理員」帳戶 (含) 以上帳戶。  
  
### <a name="to-create-and-describe-an-application-in-the-sso-database"></a>在 SSO 資料庫中建立和描述應用程式  
  
1.  建立新的 `ISSOAdmin` 物件。  
  
2.  使用對 `ISSOAdmin.CreateApplication` 的呼叫建立新的應用程式。  
  
3.  使用對 `ISSOAdmin.CreateFieldInfo` 的呼叫，新增描述應用程式的相關欄位。  
  
     在此步驟中，您需要告訴資料庫應用程式具有使用者與關聯的密碼。  
  
4.  使用對 `ISSOAdmin.UpdateApplication` 或 `ISSOAdmin2.UpdateApplication2` 的呼叫，將新建的描述推出至伺服器。  
  
     這兩個方法的差異在於 `UpdateApplication2` 是使用 `IPropertyBag` 做為描述應用程式更新的方式，而 `UpdateApplication` 則是具有多個參數。  
  
5.  藉由呼叫 `ISSOAdmin.PurgeCacheForApplication`，清除變更過的本機快取。  
  
     清理本機快取為一項安全措施，可避免在步驟 3 中描述的名稱及密碼存在一個不安全的位置中。  
  
 下列範例說明如何建立應用程式以及新增欄位資訊。  
  
```  
public static bool AddApplication(string name, string admins, string users)  
    {  
       try  
       {  
          ISSOAdmin admin=new ISSOAdmin();  
          // Create application.  
          admin.CreateApplication(name, "SSO Sample Application", "administrator@ssoaffiliateapplication.com", users, admins, SSOFlag.SSO_WINDOWS_TO_EXTERNAL | SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, 2);  
          // Add fields.  
          admin.CreateFieldInfo(name, "User Id", SSOFlag.SSO_FLAG_NONE);  
          admin.CreateFieldInfo(name, "Password", SSOFlag.SSO_FLAG_FIELD_INFO_MASK);  
          // Enable application.  
          admin.UpdateApplication(name, null, null, null, null, SSOFlag.SSO_FLAG_ENABLED, SSOFlag.SSO_FLAG_ENABLED);  
          // Purge changes.  
          admin.PurgeCacheForApplication(name);  
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
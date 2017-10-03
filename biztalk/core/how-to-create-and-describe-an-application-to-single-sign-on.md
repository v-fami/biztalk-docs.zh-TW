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
# <a name="how-to-create-and-describe-an-application-to-single-sign-on"></a><span data-ttu-id="1e1b2-102">如何建立和描述應用程式單一登入</span><span class="sxs-lookup"><span data-stu-id="1e1b2-102">How to Create and Describe an Application to Single Sign-On</span></span>
<span data-ttu-id="1e1b2-103">您需要執行的常見管理工作是將分支機構應用程式新增至「企業單一登入」(SSO) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-103">A common administrative task that you might need to perform is adding an affiliate application into the Enterprise Single Sign-On (SSO) database.</span></span> <span data-ttu-id="1e1b2-104">新增分支機構應用程式到「企業 SSO」資料庫可讓您將使用者和認證與分支機構應用程式建立關聯。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-104">Adding an affiliate application to the Enterprise SSO database enables you to associate users and credentials with the affiliated application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e1b2-105">建立分支機構應用程式需要「SSO 應用程式管理員」帳戶 (含) 以上帳戶。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-105">Creating an affiliated application requires membership in the "SSO Affiliate Administrator" account or above.</span></span>  
  
### <a name="to-create-and-describe-an-application-in-the-sso-database"></a><span data-ttu-id="1e1b2-106">在 SSO 資料庫中建立和描述應用程式</span><span class="sxs-lookup"><span data-stu-id="1e1b2-106">To create and describe an application in the SSO database</span></span>  
  
1.  <span data-ttu-id="1e1b2-107">建立新的 `ISSOAdmin` 物件。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-107">Create a new `ISSOAdmin` object.</span></span>  
  
2.  <span data-ttu-id="1e1b2-108">使用對 `ISSOAdmin.CreateApplication` 的呼叫建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-108">Create a new application with a call to `ISSOAdmin.CreateApplication`.</span></span>  
  
3.  <span data-ttu-id="1e1b2-109">使用對 `ISSOAdmin.CreateFieldInfo` 的呼叫，新增描述應用程式的相關欄位。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-109">Add the relevant fields describing the application with a call to `ISSOAdmin.CreateFieldInfo`.</span></span>  
  
     <span data-ttu-id="1e1b2-110">在此步驟中，您需要告訴資料庫應用程式具有使用者與關聯的密碼。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-110">During this step, you tell the database that an application has users and associated passwords.</span></span>  
  
4.  <span data-ttu-id="1e1b2-111">使用對 `ISSOAdmin.UpdateApplication` 或 `ISSOAdmin2.UpdateApplication2` 的呼叫，將新建的描述推出至伺服器。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-111">Push the newly created description out to the server with a call to `ISSOAdmin.UpdateApplication` or `ISSOAdmin2.UpdateApplication2`.</span></span>  
  
     <span data-ttu-id="1e1b2-112">這兩個方法的差異在於 `UpdateApplication2` 是使用 `IPropertyBag` 做為描述應用程式更新的方式，而 `UpdateApplication` 則是具有多個參數。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-112">The difference between the two methods is that `UpdateApplication2` uses an `IPropertyBag` as the way to describe the application updates, while `UpdateApplication` has multiple parameters.</span></span>  
  
5.  <span data-ttu-id="1e1b2-113">藉由呼叫 `ISSOAdmin.PurgeCacheForApplication`，清除變更過的本機快取。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-113">Purge the local cache for the changes you made by calling `ISSOAdmin.PurgeCacheForApplication`.</span></span>  
  
     <span data-ttu-id="1e1b2-114">清理本機快取為一項安全措施，可避免在步驟 3 中描述的名稱及密碼存在一個不安全的位置中。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-114">Purging the local cache is a security measure that prevents having the names and passwords that you describe in step 3 to exist in an unsecured location.</span></span>  
  
 <span data-ttu-id="1e1b2-115">下列範例說明如何建立應用程式以及新增欄位資訊。</span><span class="sxs-lookup"><span data-stu-id="1e1b2-115">The following example shows how to create an application and add field information.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e1b2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e1b2-116">See Also</span></span>  
 [<span data-ttu-id="1e1b2-117">使用企業單一登入進行程式設計</span><span class="sxs-lookup"><span data-stu-id="1e1b2-117">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)
---
title: 如何判斷目前的單一登入存取 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cab68dfc-27cd-4f7c-a0df-20c670306358
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16fc1d1677fa1a8859c75b43be36de9209dbac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249254"
---
# <a name="how-to-determine-current-single-sign-on-access"></a><span data-ttu-id="01805-102">如何判斷目前的單一登入存取</span><span class="sxs-lookup"><span data-stu-id="01805-102">How to Determine Current Single Sign-On Access</span></span>
<span data-ttu-id="01805-103">您需要為使用者執行的其中一個首要工作，就是判斷已為目前的使用者設定哪些附屬應用程式。</span><span class="sxs-lookup"><span data-stu-id="01805-103">One of the first tasks you might need to perform for a user is to determine what affiliated applications have already been set up for the current user.</span></span> <span data-ttu-id="01805-104">您可以呼叫 ISSOMapper.GetApplications 以執行此查詢。</span><span class="sxs-lookup"><span data-stu-id="01805-104">You can perform this query with a call to ISSOMapper.GetApplications.</span></span>  
  
### <a name="to-query-the-single-sign-on-database-for-the-applications-available-to-the-current-user"></a><span data-ttu-id="01805-105">若要查詢單一登入資料庫中目前使用者可用的應用程式</span><span class="sxs-lookup"><span data-stu-id="01805-105">To query the Single Sign-On database for the applications available to the current user</span></span>  
  
1.  <span data-ttu-id="01805-106">建立新的 `ISSOMapper` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="01805-106">Create a new instance of `ISSOMapper`.</span></span>  
  
     <span data-ttu-id="01805-107">一般而言，`ISSOMapper` 是設計用來擷取單一登入 (SSO) 資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="01805-107">In general, `ISSOMapper` is an interface designed to retrieve information from Single Sign-On (SSO).</span></span> <span data-ttu-id="01805-108">您很可能會在許多類似的查詢中使用 `ISSOMapper`。</span><span class="sxs-lookup"><span data-stu-id="01805-108">You will most likely use `ISSOMapper` in many similar queries.</span></span>  
  
2.  <span data-ttu-id="01805-109">呼叫 GetApplications 以擷取所有與目前使用者有關的應用程式。</span><span class="sxs-lookup"><span data-stu-id="01805-109">Retrieve all applications that are affiliated with the current user by calling GetApplications.</span></span>  
  
     <span data-ttu-id="01805-110">GetApplications 只會自動傳回目前使用者的附屬應用程式。</span><span class="sxs-lookup"><span data-stu-id="01805-110">GetApplications automatically returns only the affiliated applications of the current user.</span></span>  
  
 <span data-ttu-id="01805-111">下列程式碼範例將示範如何查詢「單一登入」資料庫。</span><span class="sxs-lookup"><span data-stu-id="01805-111">The following code example demonstrates how to query the Single Sign-On database.</span></span>  
  
```  
private static string[] Applications=null;  
. . .  
public static string[] GetCurrentUserApplications()  
{  
   if(Applications==null)  
   {  
      string[] descs;  
      string[] contacts;  
      ISSOMapper mapper=new ISSOMapper();  
      mapper.GetApplications(out Applications, out descs, out contacts);  
   }  
   return Applications;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="01805-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01805-112">See Also</span></span>  
 [<span data-ttu-id="01805-113">使用企業單一登入進行程式設計</span><span class="sxs-lookup"><span data-stu-id="01805-113">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)
---
title: 如何將單一登入認證對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e847bde9-7a4c-4b81-8ad6-6a7cf23d19a1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2717a990cf6ac2bac92067354afd42931c9a75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254206"
---
# <a name="how-to-map-single-sign-on-credentials"></a><span data-ttu-id="941aa-102">如何對應單一登入認證</span><span class="sxs-lookup"><span data-stu-id="941aa-102">How to Map Single Sign-On Credentials</span></span>
<span data-ttu-id="941aa-103">當您知道您的企業單一登入資料庫中具有附屬應用程式後，即可將使用者的認證對應至該應用程式。</span><span class="sxs-lookup"><span data-stu-id="941aa-103">When you know that you have affiliated applications in your Enterprise Single Sign-On database, you can map the credentials for a user to that application.</span></span> <span data-ttu-id="941aa-104">將目前使用者的認證對應至附屬應用程式時，您必須合併使用 `ISSOMapper` 和 `ISSOMapping` 介面。</span><span class="sxs-lookup"><span data-stu-id="941aa-104">Mapping the credentials of the current user to an affiliated application requires that you use a combination of the `ISSOMapper` and `ISSOMapping` interfaces.</span></span>  
  
### <a name="to-map-between-an-affiliated-application-and-user-credentials"></a><span data-ttu-id="941aa-105">在附屬應用程式和使用者認證之間進行對應</span><span class="sxs-lookup"><span data-stu-id="941aa-105">To map between an affiliated application and user credentials</span></span>  
  
1.  <span data-ttu-id="941aa-106">建立 `ISSOMapper` 和 `ISSOMapping` 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="941aa-106">Create new instances of `ISSOMapper` and `ISSOMapping`.</span></span>  
  
2.  <span data-ttu-id="941aa-107">將 `ISSOMapping` 屬性設定為相關的值。</span><span class="sxs-lookup"><span data-stu-id="941aa-107">Set the `ISSOMapping` properties to the relevant values.</span></span>  
  
     <span data-ttu-id="941aa-108">`ISSOMapping` 的相關屬性就是使用者的 Microsoft® Windows® 網域名稱、Windows 使用者名稱、附屬應用程式的名稱，以及外部使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="941aa-108">The relevant properties for `ISSOMapping` are the Microsoft Windows domain name of the user, the Windows user name, the name of the affiliated application, and the external user name.</span></span>  
  
3.  <span data-ttu-id="941aa-109">呼叫 ISSOMapping.Create 以建立對應。</span><span class="sxs-lookup"><span data-stu-id="941aa-109">Create the mapping with a call to ISSOMapping.Create.</span></span>  
  
     <span data-ttu-id="941aa-110">呼叫 `ISSOMapping.Create` 會將對應的本機複本傳送至企業單一登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="941aa-110">Calling `ISSOMapping.Create` propagates the local copy of the mapping out to the Enterprise Single Sign-On server.</span></span>  
  
4.  <span data-ttu-id="941aa-111">呼叫 `ISSOMapper.SetExternalCredentials` 以設定對應的認證。</span><span class="sxs-lookup"><span data-stu-id="941aa-111">Set the credentials on the mapping with a call to `ISSOMapper.SetExternalCredentials`.</span></span>  
  
5.  <span data-ttu-id="941aa-112">呼叫 `ISSOMapping.Enable` 以啟用對應。</span><span class="sxs-lookup"><span data-stu-id="941aa-112">Enable the mapping with a call to `ISSOMapping.Enable`.</span></span>  
  
 <span data-ttu-id="941aa-113">下列範例說明如何在指定的企業單一登入應用程式與使用者之間新增對應。</span><span class="sxs-lookup"><span data-stu-id="941aa-113">The following example shows how to add mapping between a specified Enterprise Single Sign-On application and a user.</span></span>  
  
```  
public static bool AddMapping(string application, string user, string XU, string XP)  
{  
   try  
   {  
      // Set mapping.  
      ISSOMapper mapper=new ISSOMapper();  
      ISSOMapping mapping=new ISSOMapping();  
     string username=user.Substring(user.IndexOf('\\')+1);  
      string userdomain=user.Substring(0, user.IndexOf('\\'));  
      mapping.WindowsDomainName=userdomain;  
      mapping.WindowsUserName=username;  
      mapping.ApplicationName=application;  
      mapping.ExternalUserName=XU;  
      mapping.Create(0);  
      // Set credentials.  
      string[] credentials=new string[]{XP};  
      mapper.SetExternalCredentials(application, XU, ref credentials);  
      mapping.Enable(0);  
   }  
   catch  
   {  
      return false;  
   }  
   return true;  
      }  
```  
  
## <a name="see-also"></a><span data-ttu-id="941aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="941aa-114">See Also</span></span>  
 [<span data-ttu-id="941aa-115">使用企業單一登入進行程式設計</span><span class="sxs-lookup"><span data-stu-id="941aa-115">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)
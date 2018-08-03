---
title: 如何建立使用者對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], creating
- managing [SSO maps], creating user maps
ms.assetid: c2e9f0db-920b-4d89-8e1e-5dc92805fd23
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 493f9b505288ea10e48eb0cf8607a870b5509425
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009887"
---
# <a name="how-to-create-user-mappings"></a><span data-ttu-id="0db1b-102">如何建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="0db1b-102">How to Create User Mappings</span></span>
<span data-ttu-id="0db1b-103">使用此命令可建立一或多個使用者對應，如 XML 檔案所指定。</span><span class="sxs-lookup"><span data-stu-id="0db1b-103">Use this command to create one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="0db1b-104">以下是 XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="0db1b-104">The following is an example XML file.</span></span>  
  
```  
<sso>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name1</externalApplication>   
<externalUserId>App1UserName</externalUserId>   
</mapping>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name2</externalApplication>   
<externalUserId>App2UserName</externalUserId>   
</mapping>  
</sso>  
  
```  
  
 <span data-ttu-id="0db1b-105">如果使用者帳戶已變更，您必須使用此命令為新的使用者帳戶建立對應。</span><span class="sxs-lookup"><span data-stu-id="0db1b-105">If a user account is changed, you must use this command to create a mapping for the new user account.</span></span> <span data-ttu-id="0db1b-106">您也必須移除舊的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="0db1b-106">You should also remove the old user mapping.</span></span> <span data-ttu-id="0db1b-107">如需有關移除對應的詳細資訊，請參閱 <<c0> [ 如何刪除使用者對應](../core/how-to-delete-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="0db1b-107">For more information about removing a mapping, see [How to Delete User Mappings](../core/how-to-delete-user-mappings.md).</span></span>  
  
 <span data-ttu-id="0db1b-108">建立使用者對應之後，您必須先啟用，才能在 SSO 系統中使用這個對應。</span><span class="sxs-lookup"><span data-stu-id="0db1b-108">After you create a user mapping, you must enable it before you can use this mapping in the SSO system.</span></span> <span data-ttu-id="0db1b-109">如需詳細資訊，請參閱 <<c0> [ 如何啟用使用者對應](../core/how-to-enable-a-user-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="0db1b-109">For more information, see [How to Enable a User Mapping](../core/how-to-enable-a-user-mapping.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0db1b-110">只有網域群組支援使用者對應。</span><span class="sxs-lookup"><span data-stu-id="0db1b-110">Only domain groups are supported for user mappings.</span></span>  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a><span data-ttu-id="0db1b-111">使用管理公用程式建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="0db1b-111">To create user mappings using the administration utility</span></span>  
  
1. <span data-ttu-id="0db1b-112">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="0db1b-112">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="0db1b-113">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="0db1b-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0db1b-114">預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0db1b-114">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="0db1b-115">類型 * * ssomanage – createmappings *\<對應檔名\>**<em>，其中 *\<對應檔名\></em>是包含您想要的使用者對應的檔案名稱若要建立。</span><span class="sxs-lookup"><span data-stu-id="0db1b-115">Type **ssomanage –createmappings *\<mappings file name\>**<em>, where *\<mappings file name\></em> is the name of file that contains the user mapping(s) you want to create.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0db1b-116">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="0db1b-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a><span data-ttu-id="0db1b-117">使用用戶端公用程式建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="0db1b-117">To create user mappings using the client utility</span></span>  
  
1. <span data-ttu-id="0db1b-118">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="0db1b-118">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="0db1b-119">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="0db1b-119">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="0db1b-120">預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="0db1b-120">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="0db1b-121">類型 * * ssoclient-setcredentials *\<應用程式名稱\> ** <em>，其中 *\<應用程式名稱\></em>是使用者想要的分支機構應用程式的名稱建立的對應。</span><span class="sxs-lookup"><span data-stu-id="0db1b-121">Type **ssoclient –setcredentials *\<application name \>**<em>, where *\<application name \></em> is the name of affiliate application that the user wants to create a mapping for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0db1b-122">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="0db1b-122">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db1b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0db1b-123">See Also</span></span>  
 <span data-ttu-id="0db1b-124">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="0db1b-124">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="0db1b-125">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="0db1b-125">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="0db1b-126">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="0db1b-126">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
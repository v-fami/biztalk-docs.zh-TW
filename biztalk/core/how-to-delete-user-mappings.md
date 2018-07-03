---
title: 如何刪除使用者對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps [SSO], deleting
- managing [SSO maps], deleting user maps
ms.assetid: de511113-b0b0-4920-91dc-4c9e380fda58
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 034f587d8c7d87f5fa6aa7e5e33ca4ef147d9f9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014383"
---
# <a name="how-to-delete-user-mappings"></a><span data-ttu-id="873d2-102">如何刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="873d2-102">How to Delete User Mappings</span></span>
<span data-ttu-id="873d2-103">使用下列命令可刪除在 XML 檔案中指定的一或多個使用者對應。</span><span class="sxs-lookup"><span data-stu-id="873d2-103">Use these commands to delete one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="873d2-104">以下是 XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="873d2-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="873d2-105">若使用者並非應用程式使用者帳戶的成員或不存在 Active Directory 中，則應使用此命令從 SSO 資料庫移除使用者對應。</span><span class="sxs-lookup"><span data-stu-id="873d2-105">If a user is not a member of the Application Users account, or does not exist in Active Directory, you should use this command to remove the user mapping from the SSO database.</span></span>  
  
 <span data-ttu-id="873d2-106">若使用者帳戶已變更，則必須使用此命令移除舊的使用者對應，再為新的使用者帳戶建立新使用者對應。</span><span class="sxs-lookup"><span data-stu-id="873d2-106">If a user account is changed, you must use this command to remove the old user mapping, and then create a new user mapping for the new user account.</span></span> <span data-ttu-id="873d2-107">如需建立對應的詳細資訊，請參閱[如何建立使用者對應](../core/how-to-create-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="873d2-107">For more information about creating a mapping, see [How to Create User Mappings](../core/how-to-create-user-mappings.md).</span></span>  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a><span data-ttu-id="873d2-108">使用管理公用程式刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="873d2-108">To delete user mappings using the administration utility</span></span>  
  
1. <span data-ttu-id="873d2-109">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="873d2-109">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="873d2-110">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="873d2-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="873d2-111">預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="873d2-111">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="873d2-112">型別<strong>ssomanage-deletemappings *\<對應檔名\></strong><em>，其中\<</em>對應檔案名稱*\>是包含您想要刪除之使用者對應的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="873d2-112">Type <strong>ssomanage –deletemappings *\<mappings file name\></strong><em>, where \<</em>mappings file name*\> is the name of the file that contains the user mapping(s) you want to delete.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="873d2-113">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="873d2-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a><span data-ttu-id="873d2-114">使用管理公用程式刪除特定使用者對應</span><span class="sxs-lookup"><span data-stu-id="873d2-114">To delete a specific user mapping using the administration utility</span></span>  
  
1. <span data-ttu-id="873d2-115">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="873d2-115">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="873d2-116">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="873d2-116">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="873d2-117">預設的安裝目錄*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="873d2-117">The default installation directory is *\<drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="873d2-118">類型 **ssomanage-deletemapping *\<網域\>*\\*\<username\> *   *\<應用程式名稱\>**<em>，其中*\<網域\></em>是 Windows 網域使用者帳戶 *\<使用者名稱\>* 是 Windows 使用者名稱，以及\<* 應用程式名稱*\>是您要移除使用者對應的特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="873d2-118">Type **ssomanage –deletemapping *\<domain\>*\\*\<username\>* *\<application name\>**<em>, where *\<domain\></em> is the Windows domain for the user account, *\<username\>* is the Windows user name, and \<* application name*\> is the specific application for which you want to remove the user mapping.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="873d2-119">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="873d2-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="873d2-120">使用用戶端公用程式刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="873d2-120">To delete a user mapping using the client utility</span></span>  
  
1. <span data-ttu-id="873d2-121">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="873d2-121">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="873d2-122">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="873d2-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="873d2-123">預設的安裝目錄*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="873d2-123">The default installation directory is *\<drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="873d2-124">類型 * * ssoclient-deletemapping *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要移除的分支機構應用程式的名稱使用者對應。</span><span class="sxs-lookup"><span data-stu-id="873d2-124">Type **ssoclient –deletemapping *\<application name\>**<em>, where *\<application name\></em> is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="873d2-125">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="873d2-125">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="873d2-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="873d2-126">See Also</span></span>  
 <span data-ttu-id="873d2-127">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="873d2-127">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="873d2-128">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="873d2-128">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="873d2-129">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="873d2-129">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
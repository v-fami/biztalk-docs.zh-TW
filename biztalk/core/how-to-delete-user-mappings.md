---
title: 如何刪除使用者對應 |Microsoft 文件
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
ms.openlocfilehash: 03f7c1fa75b6fe7bb4c78e18c97fccd1404f89c9
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25970660"
---
# <a name="how-to-delete-user-mappings"></a><span data-ttu-id="7030c-102">如何刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="7030c-102">How to Delete User Mappings</span></span>
<span data-ttu-id="7030c-103">使用下列命令可刪除在 XML 檔案中指定的一或多個使用者對應。</span><span class="sxs-lookup"><span data-stu-id="7030c-103">Use these commands to delete one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="7030c-104">以下是 XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="7030c-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="7030c-105">若使用者並非應用程式使用者帳戶的成員或不存在 Active Directory 中，則應使用此命令從 SSO 資料庫移除使用者對應。</span><span class="sxs-lookup"><span data-stu-id="7030c-105">If a user is not a member of the Application Users account, or does not exist in Active Directory, you should use this command to remove the user mapping from the SSO database.</span></span>  
  
 <span data-ttu-id="7030c-106">若使用者帳戶已變更，則必須使用此命令移除舊的使用者對應，再為新的使用者帳戶建立新使用者對應。</span><span class="sxs-lookup"><span data-stu-id="7030c-106">If a user account is changed, you must use this command to remove the old user mapping, and then create a new user mapping for the new user account.</span></span> <span data-ttu-id="7030c-107">如需有關如何建立對應的詳細資訊，請參閱[如何建立使用者對應](../core/how-to-create-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="7030c-107">For more information about creating a mapping, see [How to Create User Mappings](../core/how-to-create-user-mappings.md).</span></span>  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a><span data-ttu-id="7030c-108">使用管理公用程式刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="7030c-108">To delete user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="7030c-109">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="7030c-109">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="7030c-110">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="7030c-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7030c-111">預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="7030c-111">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="7030c-112">型別 **ssomanage – deletemappings *\<對應檔案名稱\>* * *，其中\<* 對應檔案名稱*\>是包含的檔案名稱您想要刪除的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="7030c-112">Type **ssomanage –deletemappings *\<mappings file name\>***, where \<* mappings file name*\> is the name of the file that contains the user mapping(s) you want to delete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7030c-113">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="7030c-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a><span data-ttu-id="7030c-114">使用管理公用程式刪除特定使用者對應</span><span class="sxs-lookup"><span data-stu-id="7030c-114">To delete a specific user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="7030c-115">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="7030c-115">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="7030c-116">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="7030c-116">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7030c-117">預設安裝目錄是*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="7030c-117">The default installation directory is *\<drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="7030c-118">型別 **ssomanage-deletemapping *\<網域\>*\\*\<username\> *  *\<應用程式名稱\>* * *，其中*\<網域\>* 是 Windows 網域使用者帳戶，  *\<的使用者名稱\>* 是 Windows 使用者名稱和\<* 應用程式名稱*\>是您要移除使用者對應的特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="7030c-118">Type **ssomanage –deletemapping *\<domain\>*\\*\<username\>* *\<application name\>***, where *\<domain\>* is the Windows domain for the user account, *\<username\>* is the Windows user name, and \<* application name*\> is the specific application for which you want to remove the user mapping.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7030c-119">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="7030c-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="7030c-120">使用用戶端公用程式刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="7030c-120">To delete a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="7030c-121">在 **啟動** ] 功能表上，按一下 [ **執行**, ，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="7030c-121">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="7030c-122">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="7030c-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7030c-123">預設安裝目錄是*\<磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="7030c-123">The default installation directory is *\<drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="7030c-124">型別 * * ssoclient – deletemapping *\<應用程式名稱\>* * *，其中*\<應用程式名稱\>* 是您想要移除的使用者對應的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="7030c-124">Type **ssoclient –deletemapping *\<application name\>***, where *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7030c-125">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="7030c-125">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7030c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7030c-126">See Also</span></span>  
 <span data-ttu-id="7030c-127">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="7030c-127">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="7030c-128">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="7030c-128">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="7030c-129">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="7030c-129">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
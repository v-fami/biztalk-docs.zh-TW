---
title: 如何刪除使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c4cdff-b82d-4cfd-8e20-220a2fe78656
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: a9d0a31c3dbc9d5980f59d9f30d20ec15f603a38
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-delete-user-mappings"></a><span data-ttu-id="e773d-102">如何刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="e773d-102">How to Delete User Mappings</span></span>
<span data-ttu-id="e773d-103">使用下列命令可刪除在 XML 檔案中指定的一或多個使用者對應。</span><span class="sxs-lookup"><span data-stu-id="e773d-103">Use these commands to delete one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="e773d-104">以下是 XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="e773d-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="e773d-105">如果使用者不是應用程式使用者帳戶的成員，或不存在於 Active Directory，您應該使用此命令從認證資料庫中移除使用者對應。</span><span class="sxs-lookup"><span data-stu-id="e773d-105">If a user is not a member of the Application Users account, or does not exist in Active Directory, you should use this command to remove the user mapping from the Credential database.</span></span>  
  
 <span data-ttu-id="e773d-106">若使用者帳戶已變更，則必須使用此命令移除舊的使用者對應，再為新的使用者帳戶建立新使用者對應。</span><span class="sxs-lookup"><span data-stu-id="e773d-106">If a user account is changed, you must use this command to remove the old user mapping, and then create a new user mapping for the new user account.</span></span> <span data-ttu-id="e773d-107">如需有關如何建立對應的詳細資訊，請參閱[如何建立使用者對應](../esso/how-to-create-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="e773d-107">For more information about creating a mapping, see [How to Create User Mappings](../esso/how-to-create-user-mappings.md).</span></span>  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a><span data-ttu-id="e773d-108">使用管理公用程式刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="e773d-108">To delete user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="e773d-109">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e773d-109">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="e773d-110">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e773d-110">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="e773d-111">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e773d-111">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e773d-112">型別`ssomanage –deletemappings <mappings file name>`，其中\<*對應檔案名稱*> 是包含您想要刪除的使用者對應的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e773d-112">Type `ssomanage –deletemappings <mappings file name>`, where \<*mappings file name*> is the name of the file that contains the user mappings that you want to delete.</span></span>  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a><span data-ttu-id="e773d-113">使用管理公用程式刪除特定使用者對應</span><span class="sxs-lookup"><span data-stu-id="e773d-113">To delete a specific user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="e773d-114">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e773d-114">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="e773d-115">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e773d-115">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="e773d-116">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e773d-116">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e773d-117">型別`ssomanage –deletemapping <domain>\<username> <application name>`，其中*\<網域 >*是 Windows 網域使用者帳戶， *\<使用者名稱 >*是 Windows 使用者名稱和\< *應用程式名稱*> 是您要移除使用者對應的特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="e773d-117">Type `ssomanage –deletemapping <domain>\<username> <application name>`, where *\<domain>* is the Windows domain for the user account, *\<username>* is the Windows user name, and \<*application name*> is the specific application for which you want to remove the user mapping.</span></span>  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="e773d-118">使用用戶端公用程式刪除使用者對應</span><span class="sxs-lookup"><span data-stu-id="e773d-118">To delete a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="e773d-119">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="e773d-119">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="e773d-120">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="e773d-120">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="e773d-121">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="e773d-121">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="e773d-122">型別`ssoclient –deletemapping <application name>`，其中*\<應用程式名稱 >*是您要移除使用者對應的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="e773d-122">Type `ssoclient –deletemapping <application name>`, where *\<application name>* is the name of the affiliate application for which you want to remove the user mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e773d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e773d-123">See Also</span></span>  
 <span data-ttu-id="e773d-124">[SSO 對應](../esso/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="e773d-124">[SSO Mappings](../esso/sso-mappings.md) </span></span>  
 <span data-ttu-id="e773d-125">[管理分支機構應用程式](../esso/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e773d-125">[Managing Affiliate Applications](../esso/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="e773d-126">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="e773d-126">Managing User Mappings</span></span>](../esso/managing-user-mappings.md)
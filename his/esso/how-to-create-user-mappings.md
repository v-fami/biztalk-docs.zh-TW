---
title: 如何建立使用者對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb91879c-73f4-4e9e-9e5b-534f48cd5584
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 89fd7ab2ca83d23a37944447997becd2d3f008c2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-user-mappings"></a><span data-ttu-id="f61dd-102">如何建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="f61dd-102">How to Create User Mappings</span></span>
<span data-ttu-id="f61dd-103">使用**createmappings**建立一或多個使用者對應，XML 檔案中所指定的命令。</span><span class="sxs-lookup"><span data-stu-id="f61dd-103">Use the **createmappings** command to create one or more user mappings, as specified in the XML file.</span></span> <span data-ttu-id="f61dd-104">以下是 XML 檔案的範例。</span><span class="sxs-lookup"><span data-stu-id="f61dd-104">The following is an example XML file.</span></span>  
  
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
  
 <span data-ttu-id="f61dd-105">如果使用者帳戶已變更，您必須使用此命令為新的使用者帳戶建立對應。</span><span class="sxs-lookup"><span data-stu-id="f61dd-105">If a user account is changed, you must use this command to create a mapping for the new user account.</span></span> <span data-ttu-id="f61dd-106">您也必須移除舊的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="f61dd-106">You should also remove the old user mapping.</span></span> <span data-ttu-id="f61dd-107">如需移除對應的詳細資訊，請參閱[如何刪除使用者對應](../esso/how-to-delete-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="f61dd-107">For more information about removing a mapping, see [How to Delete User Mappings](../esso/how-to-delete-user-mappings.md).</span></span>  
  
 <span data-ttu-id="f61dd-108">建立使用者對應之後，您必須啟用它，才能使用此對應單一登入 (SSO) 系統中。</span><span class="sxs-lookup"><span data-stu-id="f61dd-108">After you create a user mapping, you must enable it before you can use this mapping in the Single Sign-On (SSO) system.</span></span> <span data-ttu-id="f61dd-109">如需詳細資訊，請參閱[如何啟用使用者對應](../esso/how-to-enable-a-user-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="f61dd-109">For more information, see [How to Enable a User Mapping](../esso/how-to-enable-a-user-mapping.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f61dd-110">只有網域群組支援使用者對應。</span><span class="sxs-lookup"><span data-stu-id="f61dd-110">Only domain groups are supported for user mappings.</span></span>  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a><span data-ttu-id="f61dd-111">使用管理公用程式建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="f61dd-111">To create user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="f61dd-112">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f61dd-112">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="f61dd-113">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f61dd-113">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="f61dd-114">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="f61dd-114">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="f61dd-115">型別`ssomanage –createmappings <mappings file name>`，其中*\<對應檔案名稱 >*是包含您想要建立的使用者對應的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f61dd-115">Type `ssomanage –createmappings <mappings file name>`, where *\<mappings file name>* is the name of the file that contains the user mappings that you want to create.</span></span>  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a><span data-ttu-id="f61dd-116">使用用戶端公用程式建立使用者對應</span><span class="sxs-lookup"><span data-stu-id="f61dd-116">To create user mappings using the client utility</span></span>  
  
1.  <span data-ttu-id="f61dd-117">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f61dd-117">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="f61dd-118">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f61dd-118">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="f61dd-119">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="f61dd-119">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="f61dd-120">型別`ssoclient –setcredentials <application name >`，其中*\<應用程式名稱 >*是使用者想要建立對應的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="f61dd-120">Type `ssoclient –setcredentials <application name >`, where *\<application name >* is the name of the affiliate application that the user wants to create a mapping for.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61dd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f61dd-121">See Also</span></span>  
 <span data-ttu-id="f61dd-122">[SSO 對應](../esso/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="f61dd-122">[SSO Mappings](../esso/sso-mappings.md) </span></span>  
 <span data-ttu-id="f61dd-123">[管理分支機構應用程式](../esso/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="f61dd-123">[Managing Affiliate Applications](../esso/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="f61dd-124">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="f61dd-124">Managing User Mappings</span></span>](../esso/managing-user-mappings.md)
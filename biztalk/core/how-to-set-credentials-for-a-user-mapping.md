---
title: "如何設定認證使用者對應的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], credentials
- managing [SSO maps], configuring credentials
ms.assetid: 75b29114-56b6-4db0-8666-61cf6c675401
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4853499dbfd85cd5114212e37f4d22770d64a22
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-set-credentials-for-a-user-mapping"></a><span data-ttu-id="387d6-102">如何設定使用者對應的認證</span><span class="sxs-lookup"><span data-stu-id="387d6-102">How to Set Credentials for a User Mapping</span></span>
<span data-ttu-id="387d6-103">請使用此命令，為使用者設定認證以存取特定應用程式。</span><span class="sxs-lookup"><span data-stu-id="387d6-103">Use this command to set the credentials for a user to access a specific application.</span></span>  
  
 <span data-ttu-id="387d6-104">當您輸入此命令時，不會顯示密碼。</span><span class="sxs-lookup"><span data-stu-id="387d6-104">This command does not display the password as you type it.</span></span>  
  
 <span data-ttu-id="387d6-105">若使用者對應已經存在，此命令會為現有的對應設定認證。</span><span class="sxs-lookup"><span data-stu-id="387d6-105">If the user mapping already exists, this command sets the credentials for that existing mapping.</span></span> <span data-ttu-id="387d6-106">若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="387d6-106">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
### <a name="to-set-credentials-for-a-user-mapping"></a><span data-ttu-id="387d6-107">設定使用者對應的認證</span><span class="sxs-lookup"><span data-stu-id="387d6-107">To set credentials for a user mapping</span></span>  
  
1.  <span data-ttu-id="387d6-108">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="387d6-108">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="387d6-109">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="387d6-109">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="387d6-110">預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="387d6-110">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="387d6-111">型別**ssomanage – setcredentials\<網域\>\\< 使用者名稱\> \<applicationname\>**，其中 **\<網域\>**是 Windows 網域使用者帳戶，  **\<username\>** 是 Windows 使用者名稱和**\<應用程式名稱\>** 是特定的應用程式，您想要設定的認證。</span><span class="sxs-lookup"><span data-stu-id="387d6-111">Type **ssomanage –setcredentials \<domain\>\\<username\> \<applicationname\>**, where **\<domain\>** is the Windows domain for the user account, **\<username\>** is the Windows user name, and **\<applicationname\>** is the specific application for which you want to set the credentials for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="387d6-112">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="387d6-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
4.  <span data-ttu-id="387d6-113">當 SSO 系統提示您輸入使用者認證時，請輸入此應用程式的使用者密碼。</span><span class="sxs-lookup"><span data-stu-id="387d6-113">When the SSO system prompts you for the user credentials, enter the user password for this application.</span></span>  
  
5.  <span data-ttu-id="387d6-114">若您未建立使用者對應，SSO 系統會提示您輸入應用程式的使用者識別碼。</span><span class="sxs-lookup"><span data-stu-id="387d6-114">If you have not created the user mapping, the SSO system will prompt you for the user ID for the application.</span></span>  
  
### <a name="to-set-credentials-for-a-user-mapping-from-the-client-utility"></a><span data-ttu-id="387d6-115">從用戶端公用程式設定使用者對應的認證</span><span class="sxs-lookup"><span data-stu-id="387d6-115">To set credentials for a user mapping from the client utility</span></span>  
  
1.  <span data-ttu-id="387d6-116">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="387d6-116">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="387d6-117">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="387d6-117">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="387d6-118">預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="387d6-118">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="387d6-119">型別**ssoclient-setcredentials\<應用程式名稱\>**，其中**\<應用程式名稱\>**的分支機構應用程式名稱您要移除的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="387d6-119">Type **ssoclient -setcredentials \<application name\>**, where **\<application name\>** is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="387d6-120">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="387d6-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="387d6-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="387d6-121">See Also</span></span>  
 <span data-ttu-id="387d6-122">[如何建立使用者對應](../core/how-to-create-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="387d6-122">[How to Create User Mappings](../core/how-to-create-user-mappings.md) </span></span>  
 <span data-ttu-id="387d6-123">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="387d6-123">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="387d6-124">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="387d6-124">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="387d6-125">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="387d6-125">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
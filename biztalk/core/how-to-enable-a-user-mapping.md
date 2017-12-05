---
title: "如何啟用使用者對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enabling, user maps [SSO]
- maps [SSO], enabling
- managing [SSO maps], enabling
ms.assetid: 0f6448c9-944e-45f6-9436-87a4f3743498
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dfd87d300314616fe05a033360d84f5d2eb8b8cd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-a-user-mapping"></a><span data-ttu-id="ea556-102">如何啟用使用者對應</span><span class="sxs-lookup"><span data-stu-id="ea556-102">How to Enable a User Mapping</span></span>
<span data-ttu-id="ea556-103">您必須先啟用使用者對應，才可以使用「單一登入」系統中的對應。</span><span class="sxs-lookup"><span data-stu-id="ea556-103">You must enable a user mapping before it you can use the mapping in the Single Sign-On system.</span></span>  
  
 <span data-ttu-id="ea556-104">當您啟用使用者對應時，將會顯示為 (E) **\<網域\>\\< 使用者名稱\>**時列出使用者對應。</span><span class="sxs-lookup"><span data-stu-id="ea556-104">When you enable a user mapping, it will appear as (E) **\<domain\>\\<username\>** when you list the user mappings.</span></span>  
  
 <span data-ttu-id="ea556-105">請注意，若已使用 -setcredentials 命令來設定認證，對應便已啟用。</span><span class="sxs-lookup"><span data-stu-id="ea556-105">Note that if you have set the credentials using the -setcredentials command, the mapping will already be enabled.</span></span>  
  
### <a name="to-enable-a-user-mapping-using-the-administration-utility"></a><span data-ttu-id="ea556-106">使用管理公用程式啟用使用者對應</span><span class="sxs-lookup"><span data-stu-id="ea556-106">To enable a user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="ea556-107">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="ea556-107">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="ea556-108">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="ea556-108">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="ea556-109">預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="ea556-109">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="ea556-110">型別**ssomanage-enablemapping\<網域\>\\< 使用者名稱\>\<應用程式名稱\>**，其中 **\<網域\>**是 Windows 網域使用者帳戶，  **\<username\>** 是 Windows 使用者名稱，您要啟用認證和**\<應用程式名稱\>**是您想要移除的使用者對應，然後按 ENTER 分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea556-110">Type **ssomanage –enablemapping \<domain\>\\<username\>\<application name\>**, where **\<domain\>** is the Windows domain for the user account, **\<username\>** is the Windows user name for which you want to enable the credentials, and **\<application name\>** is the name of the affiliate application you want to remove the user mapping for and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea556-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ea556-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="ea556-112">使用用戶端公用程式啟用使用者對應</span><span class="sxs-lookup"><span data-stu-id="ea556-112">To enable a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="ea556-113">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="ea556-113">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="ea556-114">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="ea556-114">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="ea556-115">預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="ea556-115">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="ea556-116">型別**ssoclient – enablemapping\<應用程式名稱\>**，其中**\<應用程式名稱\>**是您想要的分支機構應用程式的名稱若要移除的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="ea556-116">Type **ssoclient –enablemapping \<application name\>**, where **\<application name\>** is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ea556-117">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ea556-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea556-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea556-118">See Also</span></span>  
 <span data-ttu-id="ea556-119">[如何建立使用者對應](../core/how-to-create-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="ea556-119">[How to Create User Mappings](../core/how-to-create-user-mappings.md) </span></span>  
 <span data-ttu-id="ea556-120">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="ea556-120">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="ea556-121">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ea556-121">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="ea556-122">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="ea556-122">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
---
title: "如何停用使用者對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, maps
- managing [SSO maps], disabling
- maps [SSO], disabling
ms.assetid: 9b6eaff2-674b-49f7-8d5c-3e040a7dc7f8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b17ab68356d5d39f3f839f736261d4a7ef79c78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-a-user-mapping"></a><span data-ttu-id="49d4f-102">如何停用使用者對應</span><span class="sxs-lookup"><span data-stu-id="49d4f-102">How to Disable a User Mapping</span></span>
<span data-ttu-id="49d4f-103">當您要關閉與特定對應關聯的所有作業時，可以停用使用者對應。</span><span class="sxs-lookup"><span data-stu-id="49d4f-103">You can disable a user mapping when you want to turn off all operations associated with a given mapping.</span></span> <span data-ttu-id="49d4f-104">您必須先停用使用者對應，才能進行移除。</span><span class="sxs-lookup"><span data-stu-id="49d4f-104">You must disable a user mapping before you can remove it.</span></span>  
  
 <span data-ttu-id="49d4f-105">當您停用使用者對應時，將會顯示為 (D) *\<網域\>\\< 使用者名稱\>*時列出使用者對應。</span><span class="sxs-lookup"><span data-stu-id="49d4f-105">When you disable a user mapping, it will appear as (D) *\<domain\>\\<username\>* when you list the user mappings.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-administration-utility"></a><span data-ttu-id="49d4f-106">使用管理公用程式停用使用者對應</span><span class="sxs-lookup"><span data-stu-id="49d4f-106">To disable a user mapping using the administration utility</span></span>  
  
1.  <span data-ttu-id="49d4f-107">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="49d4f-107">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="49d4f-108">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="49d4f-108">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="49d4f-109">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="49d4f-109">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="49d4f-110">型別 **ssomanage-disablemapping *\<網域\>*\\*\<username\> \<應用程式名稱\>** *，其中*\<網域\>*是 Windows 網域使用者帳戶和 *\<username\>* 是您要停用認證的 Windows 使用者名稱和*\<應用程式名稱\>*是您想要移除的使用者對應的分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="49d4f-110">Type **ssomanage –disablemapping *\<domain\>*\\*\<username\> \<application name\>***, where *\<domain\>* is the Windows domain for the user account, and *\<username\>* is the Windows user name for which you want to disable the credentials, and *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49d4f-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="49d4f-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-disable-a-user-mapping-using-the-client-utility"></a><span data-ttu-id="49d4f-112">使用用戶端公用程式停用使用者對應</span><span class="sxs-lookup"><span data-stu-id="49d4f-112">To disable a user mapping using the client utility</span></span>  
  
1.  <span data-ttu-id="49d4f-113">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="49d4f-113">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="49d4f-114">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="49d4f-114">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="49d4f-115">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="49d4f-115">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="49d4f-116">型別**ssoclient – disablemapping *\<應用程式名稱\>***，其中*\<應用程式名稱\>*是您想要移除的使用者對應的分支機構應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="49d4f-116">Type **ssoclient –disablemapping *\<application name\>***, where *\<application name\>* is the name of the affiliate application you want to remove the user mapping for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="49d4f-117">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="49d4f-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d4f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="49d4f-118">See Also</span></span>  
 <span data-ttu-id="49d4f-119">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="49d4f-119">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="49d4f-120">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="49d4f-120">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="49d4f-121">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="49d4f-121">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
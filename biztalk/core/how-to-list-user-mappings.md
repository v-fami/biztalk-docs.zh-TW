---
title: "如何列出使用者對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO maps], listing maps
- maps [SSO], listing maps
ms.assetid: f9b73785-3a59-45c8-9e88-d2d16b5a46aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6041b40c2b6a3fa468462478754079d41881bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-user-mappings"></a><span data-ttu-id="ffa44-102">如何列出使用者對應</span><span class="sxs-lookup"><span data-stu-id="ffa44-102">How to List User Mappings</span></span>
<span data-ttu-id="ffa44-103">使用此命令，以列出指定使用者的全部現有對應。</span><span class="sxs-lookup"><span data-stu-id="ffa44-103">Use this command to list all the existing mappings for the specified user.</span></span>  
  
 <span data-ttu-id="ffa44-104">您必須是 SSO 系統管理員、應用程式系統管理員、SSO 分支機構系統管理員或使用者，才能執行此工作。</span><span class="sxs-lookup"><span data-stu-id="ffa44-104">You must be an SSO administrator, application administrator, SSO affiliate administrator, or user to do this task.</span></span>  
  
 <span data-ttu-id="ffa44-105">已啟用的使用者對應則會以 (E) \<*網域*>\\*\<使用者名稱 >*，而停用使用者對應會顯示為 (D) \<*網域*>\\*\<使用者名稱 >*。</span><span class="sxs-lookup"><span data-stu-id="ffa44-105">Enabled user mappings appear as (E) \<*domain*>\\*\<username>*, while disabled user mappings appear as (D) \<*domain*>\\*\<username>*.</span></span>  
  
### <a name="to-list-user-mappings-using-the-administration-utility"></a><span data-ttu-id="ffa44-106">使用管理公用程式列出使用者對應</span><span class="sxs-lookup"><span data-stu-id="ffa44-106">To list user mappings using the administration utility</span></span>  
  
1.  <span data-ttu-id="ffa44-107">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="ffa44-107">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="ffa44-108">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="ffa44-108">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="ffa44-109">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="ffa44-109">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="ffa44-110">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="ffa44-110">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="ffa44-111">型別**ssomanage – listmappings *\<網域 >\\< 使用者名稱\>*** 列出特定的使用者擁有在所屬分支機構應用程式中的所有對應到何處*\<網域 >*是 Microsoft Windows 網域使用者帳戶和*\<使用者名稱 >*是您要列出的 Windows 使用者名稱使用者對應。</span><span class="sxs-lookup"><span data-stu-id="ffa44-111">Type **ssomanage –listmappings *\<domain>\\<username\>*** to list all the mappings a given user has in the affiliate applications he/she belongs to, where *\<domain>* is the Microsoft Windows domain for the user account, and *\<username>* is the Windows user name for which you want to list the user mappings.</span></span> <span data-ttu-id="ffa44-112">如果使用者是「分支機構系統管理員」或「SSO 系統管理員」，這個命令便會列出該使用者於所有分支機構應用程式中的所有對應。</span><span class="sxs-lookup"><span data-stu-id="ffa44-112">If the user is an Affiliate Administrator or an SSO Administrator, this command will list all the mappings for that user in all the affiliate applications.</span></span>  
  
         <span data-ttu-id="ffa44-113">或</span><span class="sxs-lookup"><span data-stu-id="ffa44-113">Or</span></span>  
  
    -   <span data-ttu-id="ffa44-114">型別**ssomanage – listmappings *\<應用程式名稱 >*** 列出給定應用程式的使用者對應。</span><span class="sxs-lookup"><span data-stu-id="ffa44-114">Type **ssomanage –listmappings *\<application name>*** to list all the user mappings for a given application.</span></span>  
  
         <span data-ttu-id="ffa44-115">或</span><span class="sxs-lookup"><span data-stu-id="ffa44-115">Or</span></span>  
  
    -   <span data-ttu-id="ffa44-116">如果您是應用程式管理員，請輸入**ssomanage – listmappings *\<網域 >\\< 使用者名稱\>* *\<應用程式名稱 >*** 列出的所有對應特定的使用者擁有您身為系統管理員的分支機構應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ffa44-116">If you are an application administrator, type **ssomanage –listmappings *\<domain>\\<username\>* *\<application name>*** to list all the mappings a given user has in the affiliate applications for which you are an administrator.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffa44-117">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ffa44-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-list-user-mappings-using-the-client-utility"></a><span data-ttu-id="ffa44-118">使用用戶端公用程式列出使用者對應</span><span class="sxs-lookup"><span data-stu-id="ffa44-118">To list user mappings using the client utility</span></span>  
  
1.  <span data-ttu-id="ffa44-119">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="ffa44-119">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="ffa44-120">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="ffa44-120">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="ffa44-121">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="ffa44-121">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="ffa44-122">型別**ssoclient – listmappings**列出您所擁有的所有對應。</span><span class="sxs-lookup"><span data-stu-id="ffa44-122">Type **ssoclient –listmappings** to list all the mappings you have.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffa44-123">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ffa44-123">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa44-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffa44-124">See Also</span></span>  
 <span data-ttu-id="ffa44-125">[如何建立使用者對應](../core/how-to-create-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="ffa44-125">[How to Create User Mappings](../core/how-to-create-user-mappings.md) </span></span>  
 <span data-ttu-id="ffa44-126">[SSO 對應](../core/sso-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="ffa44-126">[SSO Mappings](../core/sso-mappings.md) </span></span>  
 <span data-ttu-id="ffa44-127">[管理分支機構應用程式](../core/managing-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ffa44-127">[Managing Affiliate Applications](../core/managing-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="ffa44-128">管理使用者對應</span><span class="sxs-lookup"><span data-stu-id="ffa44-128">Managing User Mappings</span></span>](../core/managing-user-mappings.md)
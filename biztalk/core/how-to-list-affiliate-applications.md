---
title: "如何列出分支機構應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], listing applications
- applications [SSO], listing applications
ms.assetid: b51ff597-824e-4488-a47f-3a9b3d4437c6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d01ae0a8d94b38583745ba706524c1b02c295b71
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-list-affiliate-applications"></a><span data-ttu-id="d85b9-102">如何列出分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="d85b9-102">How to List Affiliate Applications</span></span>
<span data-ttu-id="d85b9-103">使用這個命令可列出所有分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="d85b9-103">Use this command to list all the affiliate applications.</span></span> <span data-ttu-id="d85b9-104">若使用者是「應用程式系統管理員」帳戶的成員，這個命令將只顯示使用者為系統管理員的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d85b9-104">If the user is a member of the Application Administrators account, this command will only display the application for which the user is an administrator.</span></span>  
  
### <a name="to-list-affiliate-applications-using-the-administration-utility"></a><span data-ttu-id="d85b9-105">使用管理公用程式列出分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="d85b9-105">To list affiliate applications using the administration utility</span></span>  
  
1.  <span data-ttu-id="d85b9-106">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="d85b9-106">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="d85b9-107">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="d85b9-107">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="d85b9-108">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="d85b9-108">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="d85b9-109">型別**ssomanage-listapps [all]**其中**所有**這也會顯示應用程式使用的組態存放區功能是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="d85b9-109">Type **ssomanage -listapps [all]** where **all** is an optional parameter that will also display applications using the Configuration Store feature.</span></span> <span data-ttu-id="d85b9-110">如果應用程式系統管理員身分執行此命令的使用者，它只會列出其自己是系統管理員的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d85b9-110">If the user running this command is an Application administrator, it will only list the applications for which they are an administrator.</span></span> <span data-ttu-id="d85b9-111">若執行這個命令的使用者是「分支機構系統管理員」或「SSO 系統管理員」，將會列出所有分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="d85b9-111">If the user running this command is an Affiliate Administrator or an SSO Administrator, it will list all the affiliate applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d85b9-112">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d85b9-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-list-affiliate-applications-using-the-client-utility"></a><span data-ttu-id="d85b9-113">使用用戶端公用程式列出分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="d85b9-113">To list affiliate applications using the client utility</span></span>  
  
1.  <span data-ttu-id="d85b9-114">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="d85b9-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="d85b9-115">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="d85b9-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="d85b9-116">預設安裝目錄是\<*磁碟機*>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="d85b9-116">The default installation directory is \<*drive*>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="d85b9-117">型別**ssoclient – listapps**列出分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="d85b9-117">Type **ssoclient –listapps** to list the affiliate applications.</span></span> <span data-ttu-id="d85b9-118">這只會列出執行此工作的使用者為其成員的分支機構應用程式，也就是說，他們必須屬於該分支機構應用程式的應用程式使用者群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="d85b9-118">This will list only the affiliate applications that the user performing this task is a member of, i.e., they need to belong the application user group account for that affiliate application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d85b9-119">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="d85b9-119">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85b9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d85b9-120">See Also</span></span>  
 <span data-ttu-id="d85b9-121">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="d85b9-121">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="d85b9-122">[如何建立分支機構應用程式](../core/how-to-create-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="d85b9-122">[How to Create an Affiliate Application](../core/how-to-create-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="d85b9-123">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="d85b9-123">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="d85b9-124">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="d85b9-124">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
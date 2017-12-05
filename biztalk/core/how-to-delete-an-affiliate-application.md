---
title: "如何刪除分支機構應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], deleting
- managing [SSO applications], deleting
- deleting, applications [SSO]
ms.assetid: c7ec065e-ef10-49ff-a350-105dd08dc4a9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cc742b41735f31b0da43560c19df4beb4f126d6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-delete-an-affiliate-application"></a><span data-ttu-id="4bec9-102">如何刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="4bec9-102">How to Delete an Affiliate Application</span></span>
<span data-ttu-id="4bec9-103">您可以使用 MMC 嵌入式管理單元或命令列，從 SSO 資料庫刪除指定的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4bec9-103">You can use the MMC Snap-In or the command line to delete the specified affiliate application from the SSO database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4bec9-104">當您刪除分支機構應用程式時，SSO 系統會自動刪除所有與其關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="4bec9-104">When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4bec9-105">您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="4bec9-105">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="4bec9-106">若要使用 MMC 嵌入式管理單元刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="4bec9-106">To delete an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="4bec9-107">上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="4bec9-107">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="4bec9-108">在 [範圍] 窗格的 [MMC] 嵌入式管理單元，依序展開**企業單一登入**節點。</span><span class="sxs-lookup"><span data-stu-id="4bec9-108">In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="4bec9-109">以滑鼠右鍵按一下分支機構應用程式，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="4bec9-109">Right-click the affiliate application, and then click **Delete**.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="4bec9-110">使用命令列刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="4bec9-110">To delete an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="4bec9-111">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="4bec9-111">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="4bec9-112">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="4bec9-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="4bec9-113">預設安裝目錄是*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="4bec9-113">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="4bec9-114">型別**ssomanage-deleteapp *\<應用程式名稱\>***，其中*\<應用程式名稱\>*的名稱您想要從 SSO 資料庫中移除的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="4bec9-114">Type **ssomanage –deleteapp *\<application name\>***, where *\<application name\>* is the name of the affiliate application you want to remove from the SSO database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4bec9-115">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4bec9-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bec9-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="4bec9-116">See Also</span></span>  
 <span data-ttu-id="4bec9-117">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="4bec9-117">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="4bec9-118">[如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="4bec9-118">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="4bec9-119">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="4bec9-119">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="4bec9-120">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="4bec9-120">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
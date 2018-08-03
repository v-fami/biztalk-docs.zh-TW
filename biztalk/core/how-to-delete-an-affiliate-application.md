---
title: 如何刪除分支機構應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], deleting
- managing [SSO applications], deleting
- deleting, applications [SSO]
ms.assetid: c7ec065e-ef10-49ff-a350-105dd08dc4a9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97315d21e3793ec6a282deb5f8cdd69d79ab7491
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003319"
---
# <a name="how-to-delete-an-affiliate-application"></a><span data-ttu-id="91eb5-102">如何刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="91eb5-102">How to Delete an Affiliate Application</span></span>
<span data-ttu-id="91eb5-103">您可以使用 MMC 嵌入式管理單元或命令列，從 SSO 資料庫刪除指定的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="91eb5-103">You can use the MMC Snap-In or the command line to delete the specified affiliate application from the SSO database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91eb5-104">當您刪除分支機構應用程式時，SSO 系統會自動刪除所有與其關聯的對應。</span><span class="sxs-lookup"><span data-stu-id="91eb5-104">When you delete an affiliate application, the SSO system automatically deletes all mappings associated with it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91eb5-105">您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="91eb5-105">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="91eb5-106">若要使用 MMC 嵌入式管理單元刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="91eb5-106">To delete an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="91eb5-107">上**開始**功能表上，按一下**程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="91eb5-107">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="91eb5-108">在 [範圍] 窗格的 [MMC] 嵌入式管理單元，依序展開**企業單一登入**節點。</span><span class="sxs-lookup"><span data-stu-id="91eb5-108">In the scope pane of the MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="91eb5-109">以滑鼠右鍵按一下分支機構應用程式，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="91eb5-109">Right-click the affiliate application, and then click **Delete**.</span></span>  
  
### <a name="to-delete-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="91eb5-110">使用命令列刪除分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="91eb5-110">To delete an affiliate application using the command line</span></span>  
  
1. <span data-ttu-id="91eb5-111">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="91eb5-111">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="91eb5-112">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="91eb5-112">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="91eb5-113">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="91eb5-113">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="91eb5-114">類型 * * ssomanage-deleteapp *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要移除的分支機構應用程式的名稱SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="91eb5-114">Type **ssomanage –deleteapp *\<application name\>**<em>, where *\<application name\></em> is the name of the affiliate application you want to remove from the SSO database.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="91eb5-115">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="91eb5-115">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91eb5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91eb5-116">See Also</span></span>  
 <span data-ttu-id="91eb5-117">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="91eb5-117">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="91eb5-118">[如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="91eb5-118">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="91eb5-119">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="91eb5-119">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="91eb5-120">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="91eb5-120">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
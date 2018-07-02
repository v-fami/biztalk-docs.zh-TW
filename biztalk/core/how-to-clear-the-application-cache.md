---
title: 如何清除應用程式快取 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- caching, applications
- managing [SSO applications], clearing cache
- applications [SSO], caching
ms.assetid: 6230b9a4-c7b8-47b4-854b-12853d9bf5b0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 106435fafcd9319fcee1df9bdf1b64396fa2006f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973167"
---
# <a name="how-to-clear-the-application-cache"></a><span data-ttu-id="791be-102">如何清除應用程式快取</span><span class="sxs-lookup"><span data-stu-id="791be-102">How to Clear the Application Cache</span></span>
<span data-ttu-id="791be-103">您可以使用 MMC 嵌入式管理單元或命令列，移除所有「單一登入伺服器」上特定應用程式的認證快取內容 (所有與分支機構應用程式相關的資訊)。</span><span class="sxs-lookup"><span data-stu-id="791be-103">You can use the MMC Snap-In or the command line to remove the contents of the credential cache (all the information associated with the affiliate application) for the specified application on all of the Single Sign-On Servers.</span></span>  
  
### <a name="to-clear-the-cache-using-the-mmc-snap-in"></a><span data-ttu-id="791be-104">使用 MMC 嵌入式管理單元清除快取</span><span class="sxs-lookup"><span data-stu-id="791be-104">To clear the cache using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="791be-105">在 **[開始]** 功能表上，依序按一下 **[所有程式]** 及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="791be-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="791be-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="791be-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="791be-107">按一下 **分支機構應用程式**。</span><span class="sxs-lookup"><span data-stu-id="791be-107">Click **Affiliate Applications**.</span></span>  
  
4.  <span data-ttu-id="791be-108">在 結果 窗格中，以滑鼠右鍵按一下分支機構應用程式，然後按一下 **清除**。</span><span class="sxs-lookup"><span data-stu-id="791be-108">In the results pane, right-click the affiliate application, and click **Clear**.</span></span>  
  
### <a name="to-clear-the-cache-using-the-command-line"></a><span data-ttu-id="791be-109">使用命令列清除快取</span><span class="sxs-lookup"><span data-stu-id="791be-109">To clear the cache using the command line</span></span>  
  
1. <span data-ttu-id="791be-110">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="791be-110">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="791be-111">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="791be-111">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="791be-112">預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="791be-112">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="791be-113">型別<strong>ssomanage-purgecache *\<應用程式名稱\></strong><em>，其中\<</em>應用程式名稱*\>名稱分支機構應用程式，您想要清除的快取。</span><span class="sxs-lookup"><span data-stu-id="791be-113">Type <strong>ssomanage –purgecache *\<application name\></strong><em>, where \<</em>application name*\> is the name of the affiliate application you want to purge the cache for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="791be-114">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="791be-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791be-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="791be-115">See Also</span></span>  
 <span data-ttu-id="791be-116">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="791be-116">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 [<span data-ttu-id="791be-117">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="791be-117">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
---
title: "如何啟用分支機構應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], enabling
- managing [SSO applications], enabling
- enabling, applications [SSO]
ms.assetid: 81c94e1b-cd3d-482e-9a78-9b1476af9e5f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a0e4776b60b81256552552c60aa1abb8abdcde8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-an-affiliate-application"></a><span data-ttu-id="b0371-102">如何啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b0371-102">How to Enable an Affiliate Application</span></span>
<span data-ttu-id="b0371-103">您可以使用 MMC 嵌入式管理單元或命令列，啟用指定的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0371-103">You can use the MMC Snap-In or the command line to enable the specified affiliate application.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="b0371-104">若要使用 MMC 嵌入式管理單元啟用分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b0371-104">To enable an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="b0371-105">在 **[開始]** 功能表上，依序按一下 **[所有程式]**及 **[Microsoft 企業單一登入]**，然後按一下 **[SSO 管理]**。</span><span class="sxs-lookup"><span data-stu-id="b0371-105">On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="b0371-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="b0371-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="b0371-107">以滑鼠右鍵按一下分支機構應用程式，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="b0371-107">Right-click the affililate application, and then click **Enable**.</span></span>  
  
### <a name="to-enable-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="b0371-108">若要啟用分支機構應用程式，使用命令列</span><span class="sxs-lookup"><span data-stu-id="b0371-108">To enable an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="b0371-109">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="b0371-109">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="b0371-110">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="b0371-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="b0371-111">預設安裝目錄是\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="b0371-111">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="b0371-112">型別**ssomanage-enableapp *\<應用程式名稱\>***，其中\<*應用程式名稱*\>的名稱您想要啟用分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0371-112">Type **ssomanage –enableapp *\<application name\>***, where \<*application name*\> is the name of the affiliate application you want to enable.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0371-113">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="b0371-113">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0371-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0371-114">See Also</span></span>  
 <span data-ttu-id="b0371-115">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="b0371-115">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="b0371-116">[如何建立分支機構應用程式](../core/how-to-create-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="b0371-116">[How to Create an Affiliate Application](../core/how-to-create-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="b0371-117">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="b0371-117">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="b0371-118">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="b0371-118">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)
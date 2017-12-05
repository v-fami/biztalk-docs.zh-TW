---
title: "如何管理密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], managing
- managing [SSO], disabling features
- managing [SSO], enabling features
- Password Synchronization [SSO], SSOMANAGE command line utility
- SSO database, SSOMANAGE command line utility
- managing, Password Synchronization [SSO]
- SSO database, database settings
- SSOMANAGE command line utility
ms.assetid: 033e63f2-e5b0-4400-99c3-145679d9b84e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce76f2ca16cca44af1658983c49d11f6931e931
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-password-synchronization"></a><span data-ttu-id="f9b81-102">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="f9b81-102">How to Manage Password Synchronization</span></span>
<span data-ttu-id="f9b81-103">使用 MMC 嵌入式管理單元或 SSOMANAGE 命令列公用程式來啟用或停用 SSO 功能，以及顯示目前的 SSO 資料庫設定。</span><span class="sxs-lookup"><span data-stu-id="f9b81-103">Use the MMC Snap-in or the SSOMANAGE command line utility to enable or disable SSO features, and to display current SSO database settings.</span></span>  
  
### <a name="to-manage-features-or-display-settings-using-the-mmc-snap-in"></a><span data-ttu-id="f9b81-104">使用 MMC 嵌入式管理單元管理功能或顯示設定</span><span class="sxs-lookup"><span data-stu-id="f9b81-104">To manage features or display settings using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="f9b81-105">使用滑鼠右鍵按一下適當的功能或資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9b81-105">Right-click the appropriate feature or database.</span></span>  
  
2.  <span data-ttu-id="f9b81-106">按一下適當的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="f9b81-106">Click the appropriate menu item.</span></span>  
  
### <a name="to-enable-sso-features-using-the-command-line"></a><span data-ttu-id="f9b81-107">使用命令列啟用 SSO 功能</span><span class="sxs-lookup"><span data-stu-id="f9b81-107">To enable SSO features using the command line</span></span>  
  
1.  <span data-ttu-id="f9b81-108">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="f9b81-108">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="f9b81-109">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="f9b81-109">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f9b81-110">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f9b81-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="f9b81-111">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="f9b81-111">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="f9b81-112">型別**ssomanage-啟用**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="f9b81-112">Type **ssomanage -enable** and press Enter.</span></span>  
  
### <a name="to-disable-sso-features-using-the-command-line"></a><span data-ttu-id="f9b81-113">使用命令列停用 SSO 功能</span><span class="sxs-lookup"><span data-stu-id="f9b81-113">To disable SSO features using the command line</span></span>  
  
1.  <span data-ttu-id="f9b81-114">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="f9b81-114">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="f9b81-115">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="f9b81-115">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f9b81-116">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f9b81-116">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="f9b81-117">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="f9b81-117">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="f9b81-118">型別**ssomanage-停用**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="f9b81-118">Type **ssomanage -disable** and press Enter.</span></span>  
  
### <a name="to-display-current-database-settings-using-the-command-line"></a><span data-ttu-id="f9b81-119">使用命令列顯示目前的資料庫設定</span><span class="sxs-lookup"><span data-stu-id="f9b81-119">To display current database settings using the command line</span></span>  
  
1.  <span data-ttu-id="f9b81-120">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="f9b81-120">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="f9b81-121">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="f9b81-121">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f9b81-122">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="f9b81-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="f9b81-123">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="f9b81-123">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="f9b81-124">型別**ssomanage-displaydb**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="f9b81-124">Type **ssomanage -displaydb** and press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b81-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b81-125">See Also</span></span>  
 [<span data-ttu-id="f9b81-126">密碼同步</span><span class="sxs-lookup"><span data-stu-id="f9b81-126">Password Synchronization</span></span>](../core/password-synchronization2.md)
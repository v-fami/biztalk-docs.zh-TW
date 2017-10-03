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
ms.openlocfilehash: 2939fd0594c878e3a5f1416d0b1e871b78ba3858
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-password-synchronization"></a><span data-ttu-id="7b336-102">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="7b336-102">How to Manage Password Synchronization</span></span>
<span data-ttu-id="7b336-103">使用 MMC 嵌入式管理單元或 SSOMANAGE 命令列公用程式來啟用或停用 SSO 功能，以及顯示目前的 SSO 資料庫設定。</span><span class="sxs-lookup"><span data-stu-id="7b336-103">Use the MMC Snap-in or the SSOMANAGE command line utility to enable or disable SSO features, and to display current SSO database settings.</span></span>  
  
### <a name="to-manage-features-or-display-settings-using-the-mmc-snap-in"></a><span data-ttu-id="7b336-104">使用 MMC 嵌入式管理單元管理功能或顯示設定</span><span class="sxs-lookup"><span data-stu-id="7b336-104">To manage features or display settings using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="7b336-105">使用滑鼠右鍵按一下適當的功能或資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b336-105">Right-click the appropriate feature or database.</span></span>  
  
2.  <span data-ttu-id="7b336-106">按一下適當的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="7b336-106">Click the appropriate menu item.</span></span>  
  
### <a name="to-enable-sso-features-using-the-command-line"></a><span data-ttu-id="7b336-107">使用命令列啟用 SSO 功能</span><span class="sxs-lookup"><span data-stu-id="7b336-107">To enable SSO features using the command line</span></span>  
  
1.  <span data-ttu-id="7b336-108">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="7b336-108">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="7b336-109">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="7b336-109">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="7b336-110">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="7b336-110">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7b336-111">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="7b336-111">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="7b336-112">型別**ssomanage-啟用**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="7b336-112">Type **ssomanage -enable** and press Enter.</span></span>  
  
### <a name="to-disable-sso-features-using-the-command-line"></a><span data-ttu-id="7b336-113">使用命令列停用 SSO 功能</span><span class="sxs-lookup"><span data-stu-id="7b336-113">To disable SSO features using the command line</span></span>  
  
1.  <span data-ttu-id="7b336-114">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="7b336-114">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="7b336-115">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="7b336-115">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="7b336-116">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="7b336-116">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7b336-117">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="7b336-117">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="7b336-118">型別**ssomanage-停用**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="7b336-118">Type **ssomanage -disable** and press Enter.</span></span>  
  
### <a name="to-display-current-database-settings-using-the-command-line"></a><span data-ttu-id="7b336-119">使用命令列顯示目前的資料庫設定</span><span class="sxs-lookup"><span data-stu-id="7b336-119">To display current database settings using the command line</span></span>  
  
1.  <span data-ttu-id="7b336-120">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="7b336-120">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="7b336-121">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="7b336-121">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="7b336-122">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="7b336-122">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="7b336-123">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="7b336-123">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="7b336-124">型別**ssomanage-displaydb**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="7b336-124">Type **ssomanage -displaydb** and press Enter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b336-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b336-125">See Also</span></span>  
 [<span data-ttu-id="7b336-126">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="7b336-126">Password Synchronization</span></span>](../core/password-synchronization2.md)
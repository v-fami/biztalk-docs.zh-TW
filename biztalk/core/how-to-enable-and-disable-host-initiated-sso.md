---
title: "如何啟用和停用主控件初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, disabling
- disabling, host initiated SSO
- enabling, host initiated SSO
- host initiated SSO, enabling
ms.assetid: a11d314a-6ff9-4d0a-89c3-c412541c2cec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e5783893bbc9091d0a5f1fb3f116b17413bc5d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-and-disable-host-initiated-sso"></a><span data-ttu-id="5b1ab-102">如何啟用和停用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="5b1ab-102">How to Enable and Disable Host Initiated SSO</span></span>
<span data-ttu-id="5b1ab-103">依照預設，主控件初始化的單一登入不會在單一登入系統中啟用，且必須由 SSO 系統管理員啟用。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-103">By default, host initiated Single Sign-On is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.</span></span>  
  
### <a name="to-enable-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="5b1ab-104">使用 MMC 嵌入式管理單元啟用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="5b1ab-104">To enable host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="5b1ab-105">上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-105">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="5b1ab-106">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-106">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="5b1ab-107">使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-107">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5b1ab-108">按一下**選項** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-108">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="5b1ab-109">選取**啟用主控件初始化的 SSO**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-109">Select the **Enable host initiated SSO** box, and click **OK**.</span></span>  
  
### <a name="to-enable-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="5b1ab-110">使用命令列啟用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="5b1ab-110">To enable host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="5b1ab-111">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-111">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="5b1ab-112">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-112">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5b1ab-113">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-113">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="5b1ab-114">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-114">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="5b1ab-115">型別**ssomanage-啟用 hisso**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-115">Type **ssomanage -enable hisso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5b1ab-116">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="5b1ab-117">停用 SSO 會套用至整個 SSO 系統，所有與主控件初始化的 SSO 相關的作業都會關閉。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-117">Disabling SSO applies to the entire SSO system, and all operations related to host initiated SSO are turned off.</span></span>  
  
#### <a name="to-disable-host-initiated-sso-using-the-mmc-snap-in"></a><span data-ttu-id="5b1ab-118">使用 MMC 嵌入式管理單元停用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="5b1ab-118">To disable host initiated SSO using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="5b1ab-119">上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-119">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="5b1ab-120">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-120">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="5b1ab-121">使用滑鼠右鍵按一下 **[系統]**，然後按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-121">Right-click **System**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="5b1ab-122">按一下**選項** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-122">Click the **Options** tab.</span></span>  
  
5.  <span data-ttu-id="5b1ab-123">清除**啟用主控件初始化的 SSO**方塊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-123">Clear the **Enable host initiated SSO** box, and click **OK**.</span></span>  
  
#### <a name="to-disable-host-initiated-sso-using-the-command-line"></a><span data-ttu-id="5b1ab-124">使用命令列停用主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="5b1ab-124">To disable host initiated SSO using the command line</span></span>  
  
1.  <span data-ttu-id="5b1ab-125">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-125">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="5b1ab-126">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-126">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="5b1ab-127">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-127">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="5b1ab-128">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-128">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="5b1ab-129">型別**ssomanage-停用 hisso**依適當情況。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-129">Type **ssomanage -disable hisso** as appropriate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5b1ab-130">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="5b1ab-130">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b1ab-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b1ab-131">See Also</span></span>  
 [<span data-ttu-id="5b1ab-132">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="5b1ab-132">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)
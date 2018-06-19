---
title: 安裝 SSO 管理元件 |Microsoft 文件
description: 若要取得 SSO 管理自訂安裝和使用 ssomanage 或 SSO 管理 BizTalk Server 中輸入伺服器名稱
ms.custom: ''
ms.date: 09/27/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 096839e2-7129-498d-92ee-5afeea8dbe0d
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab2bb01defe700408a551a144eae67d0405565f4
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2017
ms.locfileid: "22317983"
---
# <a name="how-to-install-the-sso-administration-component"></a><span data-ttu-id="29d61-103">如何安裝 SSO 管理元件</span><span class="sxs-lookup"><span data-stu-id="29d61-103">How to Install the SSO Administration Component</span></span>

## <a name="overview"></a><span data-ttu-id="29d61-104">概觀</span><span class="sxs-lookup"><span data-stu-id="29d61-104">Overview</span></span>
<span data-ttu-id="29d61-105">您可以安裝企業單一登入的管理元件當做獨立功能。</span><span class="sxs-lookup"><span data-stu-id="29d61-105">You can install the Enterprise Single Sign-On Administration component as a stand-alone feature.</span></span> <span data-ttu-id="29d61-106">若您需要以遠端方式管理 SSO 系統，這將非常有用。</span><span class="sxs-lookup"><span data-stu-id="29d61-106">This is useful if you need to administer the SSO system remotely.</span></span> <span data-ttu-id="29d61-107">軟硬體需求與一般「企業 SSO 執行階段服務」安裝一樣。</span><span class="sxs-lookup"><span data-stu-id="29d61-107">The hardware and software requirements are the same as for a typical Enterprise SSO Runtime Services installation.</span></span>  
  
 <span data-ttu-id="29d61-108">安裝管理元件之後, 您可以輸入要用於管理 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="29d61-108">After installing the administration component, you enter the SSO Server to be used for management.</span></span> <span data-ttu-id="29d61-109">您可以使用命令列工具 (ssomanage.exe)，或 SSO 管理 MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="29d61-109">You can do this with either the command line tool (ssomanage.exe), or the SSO Administration MMC Snap-In.</span></span> <span data-ttu-id="29d61-110">本主題會列出兩個程序。</span><span class="sxs-lookup"><span data-stu-id="29d61-110">Both procedures are listed in this topic.</span></span>  
  
 <span data-ttu-id="29d61-111">安裝 SSO 系統管理公用程式 (ssomanage.exe) 並不會在 [開始] 功能表上建立捷徑來存取命令列公用程式。</span><span class="sxs-lookup"><span data-stu-id="29d61-111">Installing the SSO administrative utility (ssomanage.exe) does not create shortcuts on the Start menu to access the command line utilities.</span></span> <span data-ttu-id="29d61-112">若要在安裝後執行 SSO 系統管理公用程式，您必須開啟命令提示字元中，並巡覽至 SSO 目錄在`Program Files\Common Files\Enterprise Single Sign-On`。</span><span class="sxs-lookup"><span data-stu-id="29d61-112">To run the SSO administrative utilities after installation, you must open a command prompt, and navigate to the SSO directory at `Program Files\Common Files\Enterprise Single Sign-On`.</span></span>  
  
 <span data-ttu-id="29d61-113">「企業 SSO 管理」功能也包含 MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="29d61-113">The Enterprise SSO Administration feature also includes an MMC Snap-in.</span></span> <span data-ttu-id="29d61-114">嵌入式管理單元至函式，必須在電腦上安裝 MMC 3.0。</span><span class="sxs-lookup"><span data-stu-id="29d61-114">MMC 3.0 must be installed on your computer for the Snap-in to function.</span></span>  
  
 <span data-ttu-id="29d61-115">若要開啟 企業 SSO MMC 嵌入式管理單元從**啟動**功能表上，選取**所有程式**，選取**Microsoft 企業單一登入**，然後**SSO管理**。</span><span class="sxs-lookup"><span data-stu-id="29d61-115">To open the Enterprise SSO MMC Snap-in from the **Start** menu, select **All Programs**, select **Microsoft Enterprise Single Sign-On**, and then **SSO Administration**.</span></span>  
  
## <a name="install-the-enterprise-single-sign-on-administrative-component"></a><span data-ttu-id="29d61-116">安裝企業單一登入系統管理元件</span><span class="sxs-lookup"><span data-stu-id="29d61-116">Install the Enterprise Single Sign-On administrative component</span></span>  
  
-   <span data-ttu-id="29d61-117">自訂安裝的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，並選取 企業單一登入的管理功能。</span><span class="sxs-lookup"><span data-stu-id="29d61-117">Do a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and select only the Enterprise Single Sign-On Administration feature.</span></span> <span data-ttu-id="29d61-118">如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，這列在**其他軟體**。</span><span class="sxs-lookup"><span data-stu-id="29d61-118">For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], this is listed under **Additional Software**.</span></span>  
  
## <a name="enter-the-server-using-the-mmc-snap-in"></a><span data-ttu-id="29d61-119">輸入使用 MMC 嵌入式管理單元的伺服器</span><span class="sxs-lookup"><span data-stu-id="29d61-119">Enter the server using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="29d61-120">在目前未安裝管理元件的電腦上完成安裝後，開啟 SSO 管理嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="29d61-120">After installing the administrative component on a computer where it is not currently installed, open the SSO Administration Snap-In.</span></span>  
  
     <span data-ttu-id="29d61-121">在**啟動**功能表上，選取**所有程式**，選取**Microsoft 企業單一登入**，然後選取**SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="29d61-121">In the **Start** menu, select **All Programs**, select **Microsoft Enterprise Single Sign-On**, and then select **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="29d61-122">在 MMC 嵌入式管理單元在**主控台根目錄**，以滑鼠右鍵按一下**企業單一登入**，然後按一下**選取**。</span><span class="sxs-lookup"><span data-stu-id="29d61-122">In the MMC Snap-In under the **Console Root**, right-click **Enterprise Single Sign-On**, and click **Select**.</span></span>  
  
     <span data-ttu-id="29d61-123">**選取 SSO 伺服器**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="29d61-123">The **Select SSO Server** dialog box will appear.</span></span>  
  
3.  <span data-ttu-id="29d61-124">輸入或瀏覽至您要指定的 SSO 伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="29d61-124">Enter or browse to the SSO server name you want to specify.</span></span> <span data-ttu-id="29d61-125">若要指定所有使用者的 SSO 伺服器的電腦上，選取**設定所有使用者的 SSO 伺服器**。</span><span class="sxs-lookup"><span data-stu-id="29d61-125">To specify the SSO server for all users on the computer, select **Set SSO Server for all users**.</span></span>  
  
4.  <span data-ttu-id="29d61-126">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="29d61-126">Click **OK**.</span></span>  
  
## <a name="enter-the-server-using-the-command-line-tool"></a><span data-ttu-id="29d61-127">輸入伺服器使用命令列工具</span><span class="sxs-lookup"><span data-stu-id="29d61-127">Enter the server using the command line tool</span></span>  
  
1.  <span data-ttu-id="29d61-128">依序按一下 **[開始]** 及 **[執行]**，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="29d61-128">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="29d61-129">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="29d61-129">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="29d61-130">預設安裝目錄是`\Program Files\Common Files\Enterprise Single Sign-On`。</span><span class="sxs-lookup"><span data-stu-id="29d61-130">The default installation directory is `\Program Files\Common Files\Enterprise Single Sign-On`.</span></span>  
  
3.  <span data-ttu-id="29d61-131">選取下列選項的其中一個輸入 SSO 伺服器：</span><span class="sxs-lookup"><span data-stu-id="29d61-131">Enter the SSO Server by selecting one of the following options:</span></span>  
  
    1.  <span data-ttu-id="29d61-132">型別**ssomanage – server**輸入您想要執行管理作業時，連接到 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="29d61-132">Type **ssomanage –server** to enter the SSO Server you want to connect to when performing administration operations.</span></span>  
  
         <span data-ttu-id="29d61-133">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="29d61-133">\- OR -</span></span>  
  
    2.  <span data-ttu-id="29d61-134">型別**ssomanage-serverall**輸入此電腦的所有使用者執行管理作業時將會都連接到 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="29d61-134">Type **ssomanage -serverall** to enter the SSO Server all users of this computer will connect to when performing administration operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d61-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29d61-135">See Also</span></span>  
 <span data-ttu-id="29d61-136">[如何安裝 SSO 用戶端公用程式](../core/how-to-install-the-sso-client-utility.md) </span><span class="sxs-lookup"><span data-stu-id="29d61-136">[How to Install the SSO Client Utility](../core/how-to-install-the-sso-client-utility.md) </span></span>  
 <span data-ttu-id="29d61-137">[設定 SSO](../core/configuring-sso.md) </span><span class="sxs-lookup"><span data-stu-id="29d61-137">[Configuring SSO](../core/configuring-sso.md) </span></span>  
 [<span data-ttu-id="29d61-138">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="29d61-138">Installing SSO</span></span>](../core/installing-sso.md)

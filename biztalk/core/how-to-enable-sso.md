---
title: "如何啟用 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], creating
- SSO, enabling
- maps [SSO], creating
- managing [SSO], enabling
- SSO, maps
- SSO, applications
- creating, applications [SSO]
- managing [SSO], creating affiliate applications
ms.assetid: dda89d15-6b70-4c40-b658-2f6cbdd545c8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51b07bc34779643124efd5b249373301f7e47b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-sso"></a><span data-ttu-id="a20bd-102">如何啟用 SSO</span><span class="sxs-lookup"><span data-stu-id="a20bd-102">How to Enable SSO</span></span>
<span data-ttu-id="a20bd-103">使用 MMC 嵌入式管理單元或命令列，可以啟用整個企業單一登入 (SSO) 系統。</span><span class="sxs-lookup"><span data-stu-id="a20bd-103">You can enable the entire Enterprise Single Sign-On (SSO) system by using either the MMC Snap-In or the command line.</span></span>  
  
 <span data-ttu-id="a20bd-104">執行啟用命令時，在短暫延遲之後才會啟用所有單一登入伺服器，因為每個伺服器都會輪詢 SSO 資料庫以獲得最新的全域資訊。</span><span class="sxs-lookup"><span data-stu-id="a20bd-104">After you run the enabling command, there is a short delay before all Single Sign-On Servers are enabled, as each polls the SSO database for the latest global information.</span></span>  
  
 <span data-ttu-id="a20bd-105">若您要設定 SSO 系統中的分支機構應用程式與對應，則還需建立分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="a20bd-105">If you want to configure affiliate applications and mappings in the SSO system, you must also create an affiliate application.</span></span> <span data-ttu-id="a20bd-106">在 SSO 分支機構系統管理員建立分支機構應用程式之後，應用程式系統管理員可將它變更，而應用程式使用者 (一般使用者) 可建立他們自己的對應。</span><span class="sxs-lookup"><span data-stu-id="a20bd-106">After an SSO affiliate administrator creates an affiliate application, an application administrator can make changes to it, and application users (end-users) can create their own mappings.</span></span> <span data-ttu-id="a20bd-107">如需詳細資訊，請參閱[管理分支機構應用程式](../core/managing-affiliate-applications.md)和[管理使用者對應](../core/managing-user-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="a20bd-107">For more information, see [Managing Affiliate Applications](../core/managing-affiliate-applications.md) and [Managing User Mappings](../core/managing-user-mappings.md).</span></span>  
  
### <a name="to-enable-the-sso-system-using-the-mmc-snap-in"></a><span data-ttu-id="a20bd-108">若要啟用使用 MMC 嵌入式管理單元的 SSO 系統</span><span class="sxs-lookup"><span data-stu-id="a20bd-108">To enable the SSO system using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="a20bd-109">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="a20bd-109">Click **Start**, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="a20bd-110">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a20bd-110">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="a20bd-111">以滑鼠右鍵按一下**系統**，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="a20bd-111">Right-click **System**, and then click **Enable**.</span></span>  
  
### <a name="to-enable-the-sso-system-using-the-command-line"></a><span data-ttu-id="a20bd-112">使用命令列啟用 SSO 系統</span><span class="sxs-lookup"><span data-stu-id="a20bd-112">To enable the SSO system using the command line</span></span>  
  
1.  <span data-ttu-id="a20bd-113">依序按一下 **[開始]**及 **[執行]**，然後輸入 **cmd**。</span><span class="sxs-lookup"><span data-stu-id="a20bd-113">Click **Start**, click **Run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="a20bd-114">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="a20bd-114">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="a20bd-115">預設安裝目錄是**\<磁碟機 >**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="a20bd-115">The default installation directory is **\<drive>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="a20bd-116">型別**ssomanage – enablesso**。</span><span class="sxs-lookup"><span data-stu-id="a20bd-116">Type **ssomanage –enablesso**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a20bd-117">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="a20bd-117">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-enable-sso-to-create-affiliate-applications-and-mappings"></a><span data-ttu-id="a20bd-118">啟用 SSO 以建立分支機構應用程式與對應</span><span class="sxs-lookup"><span data-stu-id="a20bd-118">To enable SSO to create affiliate applications and mappings</span></span>  
  
1.  <span data-ttu-id="a20bd-119">以 SSO 系統管理員或 SSO 分支機構系統管理員身分登入 SSO 伺服器，或在擁有 SSO 的 SSO 管理子服務的電腦上登入。</span><span class="sxs-lookup"><span data-stu-id="a20bd-119">Log on as an SSO administrator or SSO affiliate administrator to the SSO Server, or on a computer that has the SSO administration sub services of SSO.</span></span>  
  
2.  <span data-ttu-id="a20bd-120">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="a20bd-120">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
3.  <span data-ttu-id="a20bd-121">在命令列提示字元中，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="a20bd-121">At the command line prompt, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="a20bd-122">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="a20bd-122">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="a20bd-123">型別**ssomanage-enablesso**啟用企業單一登入服務。</span><span class="sxs-lookup"><span data-stu-id="a20bd-123">Type **ssomanage -enablesso** to enable the Enterprise Single Sign-On service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a20bd-124">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="a20bd-124">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
5.  <span data-ttu-id="a20bd-125">以 SSO 分支機構系統管理員身分登入。</span><span class="sxs-lookup"><span data-stu-id="a20bd-125">Log on as an SSO affiliate administrator.</span></span>  
  
6.  <span data-ttu-id="a20bd-126">型別**ssomanage createapps *\<應用程式檔案 >*** 建立分支機構應用程式，其中\<應用程式檔案 > 是包含定義的 XML 檔案分支機構應用程式中。</span><span class="sxs-lookup"><span data-stu-id="a20bd-126">Type **ssomanage -createapps *\<application file>*** to create an affiliate application, where \<application file> is the XML file that contains definitions for the affiliate applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a20bd-127">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="a20bd-127">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a20bd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a20bd-128">See Also</span></span>  
 <span data-ttu-id="a20bd-129">[如何設定 SSO 伺服器](../core/how-to-set-the-sso-server.md) </span><span class="sxs-lookup"><span data-stu-id="a20bd-129">[How to Set the SSO Server](../core/how-to-set-the-sso-server.md) </span></span>  
 <span data-ttu-id="a20bd-130">[如何停用 SSO](../core/how-to-disable-sso.md) </span><span class="sxs-lookup"><span data-stu-id="a20bd-130">[How to Disable SSO](../core/how-to-disable-sso.md) </span></span>  
 <span data-ttu-id="a20bd-131">[如何更新 SSO 資料庫](../core/how-to-update-the-sso-database.md) </span><span class="sxs-lookup"><span data-stu-id="a20bd-131">[How to Update the SSO Database](../core/how-to-update-the-sso-database.md) </span></span>  
 [<span data-ttu-id="a20bd-132">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="a20bd-132">Using SSO</span></span>](../core/using-sso.md)
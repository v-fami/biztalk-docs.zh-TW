---
title: 如何安裝 SSO 用戶端公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, client utility
- client utility [SSO]
- SSO, installing
ms.assetid: e14d257e-2fde-46af-b90c-5dbc0884536b
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674ecc3857fe9e5b5cbef2914aec875f350d7de5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003959"
---
# <a name="how-to-install-the-sso-client-utility"></a><span data-ttu-id="d1d11-102">如何安裝 SSO 用戶端公用程式</span><span class="sxs-lookup"><span data-stu-id="d1d11-102">How to Install the SSO Client Utility</span></span>
<span data-ttu-id="d1d11-103">獨立的 SSO 用戶端公用程式 (命令列公用程式，以使用者介面為基礎) 讓一般使用者可以在 SSO 資料庫中設定其用戶端對應。</span><span class="sxs-lookup"><span data-stu-id="d1d11-103">The stand-alone SSO client utility (command-line utility and user interface-based) allows end users to configure their client mappings in the SSO database.</span></span> <span data-ttu-id="d1d11-104">SSO 用戶端公用程式是以自我解壓縮檔 (SSOClientInstall.exe) 的方式安裝，並且會隨 SSO 管理功能一併安裝。</span><span class="sxs-lookup"><span data-stu-id="d1d11-104">You can install the client utility from a self-extracting file (SSOClientInstall.exe) which is installed with the SSO administration feature.</span></span> <span data-ttu-id="d1d11-105">系統管理員也可將安裝程式封裝放在網路共用上，讓用戶端使用者使用安裝程式封裝。</span><span class="sxs-lookup"><span data-stu-id="d1d11-105">Administrators can also make the installer package available to client users by placing a copy of the installer package on a network share.</span></span>  
  
 <span data-ttu-id="d1d11-106">若要安裝 SSO 用戶端公用程式，用戶端電腦必須執行下列其中一種作業系統：</span><span class="sxs-lookup"><span data-stu-id="d1d11-106">To install the SSO client utility, you must be running one of the following operating systems on the client computer:</span></span>  
  
- [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
- [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)]<span data-ttu-id="d1d11-107"> 或[!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)](只有必要的時候如果您使用 UI 型 SSO 用戶端公用程式，或利用 managed 互通性元件的企業單一登入)。</span><span class="sxs-lookup"><span data-stu-id="d1d11-107"> or [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] (only necessary if you are using the UI-based SSO Client Utility or for leveraging the managed interoperability component of Enterprise SSO).</span></span>  
  
  <span data-ttu-id="d1d11-108">安裝 SSO 用戶端公用程式之後, 您可以啟動此**開始**功能表中的按一下**程式**， **Microsoft 企業單一登入**，然後**SSO 用戶端公用程式**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-108">After installing the SSO Client Utility, you can launch it from the **Start** menu by clicking **Programs**, **Microsoft Enterprise Single Sign-On**, and then **SSO Client Utility**.</span></span>  
  
### <a name="to-install-the-sso-client-utility"></a><span data-ttu-id="d1d11-109">安裝 SSO 用戶端公用程式</span><span class="sxs-lookup"><span data-stu-id="d1d11-109">To install the SSO client utility</span></span>  
  
1.  <span data-ttu-id="d1d11-110">按兩下安裝程式封裝 SSOClientInstall。</span><span class="sxs-lookup"><span data-stu-id="d1d11-110">Double-click the installer package SSOClientInstall.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d1d11-111">向您的「企業單一登入系統管理員」詢問此檔案在您企業中的位置。</span><span class="sxs-lookup"><span data-stu-id="d1d11-111">Ask your Enterprise Single Sign-On Administrator for the location of this file in your enterprise.</span></span>  
  
     <span data-ttu-id="d1d11-112">**WinZip 自我解壓縮程式**程式隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d1d11-112">The **WinZip Self-Extractor** program appears.</span></span>  
  
2.  <span data-ttu-id="d1d11-113">選取您要解壓縮檔案，然後按一下 的資料夾**解壓縮**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-113">Select the folder where you want to unzip the files, and click **Unzip**.</span></span>  
  
     <span data-ttu-id="d1d11-114">建議將檔案解壓縮至暫存資料夾。</span><span class="sxs-lookup"><span data-stu-id="d1d11-114">It is recommended to unzip the files in a temporary folder.</span></span>  
  
     <span data-ttu-id="d1d11-115">**企業單一登入用戶端安裝**程式隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d1d11-115">The **Enterprise Single Sign-On Client Setup** program appears.</span></span>  
  
3.  <span data-ttu-id="d1d11-116">在  **歡迎使用 「 企業單一登入用戶端**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-116">On **the Welcome to the Enterprise Single Sign-On Client** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="d1d11-117">在 [授權合約] 頁面中，按一下 [**我接受授權合約中的條款**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-117">On the License Agreement page, click **I accept the terms of this license agreement**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="d1d11-118">在 [**使用者資訊**頁面上，輸入您的使用者名稱、 組織名稱，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-118">On the **User Information** page, type your user name, organization name, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="d1d11-119">在 **開始安裝**頁面上，按一下**安裝**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-119">On the **Start Installation** page, click **Install**.</span></span>  
  
7.  <span data-ttu-id="d1d11-120">在 **完成企業單一登入用戶端精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-120">On the **Completing the Enterprise Single Sign-On Client Wizard** page, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="d1d11-121">執行下列其中一項動作以指定 SSO 伺服器：</span><span class="sxs-lookup"><span data-stu-id="d1d11-121">Specify the SSO server by doing either of the following:</span></span>  
  
    -   <span data-ttu-id="d1d11-122">開啟 ENTSSO 管理 MMC 嵌入式管理單元。</span><span class="sxs-lookup"><span data-stu-id="d1d11-122">Open the ENTSSO Administration MMC Snap-In.</span></span> <span data-ttu-id="d1d11-123">**選取 SSO 伺服器**對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d1d11-123">The **Select SSO Server** dialog will appear.</span></span> <span data-ttu-id="d1d11-124">輸入或瀏覽到您在執行管理作業時希望連接的 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1d11-124">Enter or browse to the SSO Server that you want to connect to when you perform administration operations.</span></span> <span data-ttu-id="d1d11-125">若要指定所有使用者的 SSO 伺服器的電腦上，選取**為所有使用者設定 SSO 伺服器**。</span><span class="sxs-lookup"><span data-stu-id="d1d11-125">To specify the SSO Server for all users on the machine, select **Set SSO Server for all users**.</span></span>  
  
         <span data-ttu-id="d1d11-126">或</span><span class="sxs-lookup"><span data-stu-id="d1d11-126">OR</span></span>  
  
    -   <span data-ttu-id="d1d11-127">在命令提示字元中，輸入`ssomanage –server`來指定所需的 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1d11-127">At a command prompt, type `ssomanage –server` to specify the SSO server desired.</span></span> <span data-ttu-id="d1d11-128">您也可以輸入`ssomanage -serverall`以指定執行管理作業時，此電腦的所有使用者會都連線到 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d1d11-128">You can also type `ssomanage -serverall` to specify the SSO server that all users of this computer will connect to when performing administration operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d11-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d11-129">See Also</span></span>  
 <span data-ttu-id="d1d11-130">[如何安裝 SSO 管理元件](../core/how-to-install-the-sso-administration-component.md) </span><span class="sxs-lookup"><span data-stu-id="d1d11-130">[How to Install the SSO Administration Component](../core/how-to-install-the-sso-administration-component.md) </span></span>  
 <span data-ttu-id="d1d11-131">[設定 SSO](../core/configuring-sso.md) </span><span class="sxs-lookup"><span data-stu-id="d1d11-131">[Configuring SSO](../core/configuring-sso.md) </span></span>  
 [<span data-ttu-id="d1d11-132">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="d1d11-132">Installing SSO</span></span>](../core/installing-sso.md)
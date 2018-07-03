---
title: 安裝 BizTalk Server 2016 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f5ac913-0734-45b2-8e25-1db146d81858
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f6c6868302554aa14d80c296955e657c9f171d6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003735"
---
# <a name="install-biztalk-server-2016"></a><span data-ttu-id="d0c06-102">安裝 BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="d0c06-102">Install BizTalk Server 2016</span></span>
<span data-ttu-id="d0c06-103">在單一電腦上安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="d0c06-103">Install BizTalk Server on a single computer.</span></span>

## <a name="before-you-get-started"></a><span data-ttu-id="d0c06-104">在開始之前</span><span class="sxs-lookup"><span data-stu-id="d0c06-104">Before you get started</span></span>

* <span data-ttu-id="d0c06-105">**系統管理員** – 當您安裝 SQL Server 時，安裝程式會自動將系統管理員權限授與您所登入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0c06-105">**System Administrator** – When you install SQL Server, setup automatically grants your signed-in account System Administrator rights.</span></span> <span data-ttu-id="d0c06-106">由於安裝 BizTalk Server 也需要這些權限，因此請執行下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="d0c06-106">Since these rights are also required to install BizTalk Server, do one of the following:</span></span>
  * <span data-ttu-id="d0c06-107">使用您在安裝 SQL Server 時所使用的相同帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0c06-107">Use the same account you used when you installed SQL Server.</span></span>
  * <span data-ttu-id="d0c06-108">將系統管理員權限授與所登入的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0c06-108">Give the signed-in account System Administrator rights.</span></span>
  * <span data-ttu-id="d0c06-109">確認所登入的帳戶是本機系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="d0c06-109">Confirm the signed-in account is a member of the local administrators group.</span></span>
* <span data-ttu-id="d0c06-110">**帳戶名稱** – 您應該盡量使用預設帳戶名稱。</span><span class="sxs-lookup"><span data-stu-id="d0c06-110">**Account names** – Use the default account names whenever possible.</span></span> <span data-ttu-id="d0c06-111">BizTalk Server 安裝程式會自動輸入預設帳戶。</span><span class="sxs-lookup"><span data-stu-id="d0c06-111">The BizTalk Server setup automatically enters the default accounts.</span></span> <span data-ttu-id="d0c06-112">如果在網域中有多個 BizTalk Server 群組，請變更帳戶名稱以避免發生衝突。</span><span class="sxs-lookup"><span data-stu-id="d0c06-112">If there are multiple BizTalk Server groups within the Domain, change the account names to avoid conflicts.</span></span> <span data-ttu-id="d0c06-113">如果您要變更名稱，BizTalk Server 只支援 *NetBIOS 網域名稱\使用者*這種名稱格式的服務帳戶和 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="d0c06-113">If you change the names, BizTalk Server supports only *NetBIOS domain name\user* for service accounts and Windows groups.</span></span>
* <span data-ttu-id="d0c06-114">**帳戶名稱與 BAM 管理 Web 服務** – BizTalk Server 不支援使用內建帳戶或無密碼的帳戶作為 BAM 管理 Web 服務使用者。</span><span class="sxs-lookup"><span data-stu-id="d0c06-114">**Account names with BAM Management Web Service** – BizTalk Server does not support built-in accounts or accounts without passwords for the BAM Management Web Service User.</span></span> <span data-ttu-id="d0c06-115">Web 服務會存取 BizTalk Server 資料庫，而這類帳戶可能會帶來安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="d0c06-115">The web service accesses the BizTalk Server database and these accounts may suggest a security threat.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="d0c06-116">使用這類帳戶來設定 BizTalk Server 可能會成功，但 BAM 管理 Web 服務會失敗。</span><span class="sxs-lookup"><span data-stu-id="d0c06-116">Configuring BizTalk Server with these typs of accounts may succeed, but the BAM Management Web Service fails.</span></span> <span data-ttu-id="d0c06-117">內建帳戶或無密碼的帳戶可用於 BAM 應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="d0c06-117">Built-in accounts or accounts without passwords can be used for the BAM Application pool.</span></span>

* <span data-ttu-id="d0c06-118">**BizTalk 組件檢視工具** – 不支援 64 位元平台。</span><span class="sxs-lookup"><span data-stu-id="d0c06-118">**BizTalk Assembly Viewer** – Not supported on a 64-bit platform.</span></span> 
* <span data-ttu-id="d0c06-119">**安裝和解除安裝** – 解除安裝 BizTalk Server 時，需要手動刪除 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d0c06-119">**Install and Uninstall** – Uninstalling BizTalk Server requires manually deleting the BizTalk Server databases.</span></span> <span data-ttu-id="d0c06-120">如果以開發人員或評估員身分來安裝 BizTalk Server，請使用虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="d0c06-120">If you are installing BizTalk Server as a developer or evaluator, use a virtual machine.</span></span> <span data-ttu-id="d0c06-121">如果需要重新安裝，您可以輕鬆復原虛擬機器，而不需要解除安裝和刪除資料庫。</span><span class="sxs-lookup"><span data-stu-id="d0c06-121">If you need to reinstall, you can easily roll back the virtual machine without having to uninstall and delete the databases.</span></span>
* <span data-ttu-id="d0c06-122">**32 位元和 64 位元電腦** – 在 32 位元或 64 位元電腦上安裝 BizTalk Server 時有幾項差異。</span><span class="sxs-lookup"><span data-stu-id="d0c06-122">**32-bit and 64-bit computers** – There are few differences when installing BizTalk Server on 32-bit or 64-bit computer.</span></span> <span data-ttu-id="d0c06-123">安裝和設定的內容涵蓋 32 位元和 64 位元的電腦，</span><span class="sxs-lookup"><span data-stu-id="d0c06-123">The installation and configuration covers 32-bit and 64-bit computers.</span></span> <span data-ttu-id="d0c06-124">但會註明任何差異。</span><span class="sxs-lookup"><span data-stu-id="d0c06-124">Any differences are noted.</span></span>
* <span data-ttu-id="d0c06-125">**工作群組** - 支援在工作群組環境中的單一電腦上安裝和設定 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="d0c06-125">**Workgroups** - Installing and configuring BizTalk Server in the workgroup environment on a single computer is supported.</span></span> <span data-ttu-id="d0c06-126">SQL Server 與 BizTalk Server 的功能和元件係在同一部電腦上安裝和設定。</span><span class="sxs-lookup"><span data-stu-id="d0c06-126">SQL Server and BizTalk Server features and components are installed and configured on the same computer.</span></span>


## <a name="install-biztalk-server"></a><span data-ttu-id="d0c06-127">安裝 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d0c06-127">Install BizTalk Server</span></span>
1. <span data-ttu-id="d0c06-128">關閉所有開啟的程式。</span><span class="sxs-lookup"><span data-stu-id="d0c06-128">Close any open programs.</span></span> <span data-ttu-id="d0c06-129">以系統管理員身分執行 BizTalk Server 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="d0c06-129">Run the BizTalk Server setup as an Administrator.</span></span>
2. <span data-ttu-id="d0c06-130">選取 [安裝 Microsoft BizTalk Server 2016]。</span><span class="sxs-lookup"><span data-stu-id="d0c06-130">Select **Install Microsoft BizTalk Server 2016**.</span></span>
3. <span data-ttu-id="d0c06-131">輸入您的 [使用者名稱]、[組織] 和產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="d0c06-131">Enter your **User name**, your **Organization**, and your product key.</span></span> <span data-ttu-id="d0c06-132">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d0c06-132">Select **Next**.</span></span>
4. <span data-ttu-id="d0c06-133">接受授權合約，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d0c06-133">Accept the license agreement, and select **Next**.</span></span>
5. <span data-ttu-id="d0c06-134">選擇參與「客戶經驗改進計畫」，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="d0c06-134">Choose to participate in the Customer Experience Improvement Program, and select **Next**.</span></span>
6. <span data-ttu-id="d0c06-135">選擇您想要安裝的元件：</span><span class="sxs-lookup"><span data-stu-id="d0c06-135">Choose which components you want to install:</span></span>

    ![bts2016install_components](../install-and-config-guides/media/bts2016install-components.gif)
  
    <span data-ttu-id="d0c06-137">請務必選取 [其他軟體]。</span><span class="sxs-lookup"><span data-stu-id="d0c06-137">Be sure to select **Additional Software**.</span></span> <span data-ttu-id="d0c06-138">您也可以變更安裝位置：</span><span class="sxs-lookup"><span data-stu-id="d0c06-138">You can also change the installation location:</span></span> 
  
    ![bts2016install_additional](../install-and-config-guides/media/bts2016install-additional.gif)

    <span data-ttu-id="d0c06-140">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d0c06-140">Select **Next**.</span></span>   
  
   7. <span data-ttu-id="d0c06-141">根據您選擇的元件，可能有一些額外的必要條件，例如 ADOMD.NET。</span><span class="sxs-lookup"><span data-stu-id="d0c06-141">Depending on the components you choose, there may be some additional prerequisites, such as ADOMD.NET.</span></span> <span data-ttu-id="d0c06-142">安裝程式會自動為您安裝所有必要的可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="d0c06-142">The setup can install all the redistributable prerequisites automatically for you.</span></span> <span data-ttu-id="d0c06-143">選項包含：</span><span class="sxs-lookup"><span data-stu-id="d0c06-143">Your options include:</span></span>
7. <span data-ttu-id="d0c06-144">**手動安裝必要的可轉散發套件**：系統會關閉安裝精靈，以便您手動安裝遺漏的必要條件。</span><span class="sxs-lookup"><span data-stu-id="d0c06-144">**Manually install the redistributable prerequisites** : The installation wizard closes so you can manually install the missing prerequisites.</span></span>
8. <span data-ttu-id="d0c06-145">**從 Web 自動安裝必要的可轉散發套件**：預設值。</span><span class="sxs-lookup"><span data-stu-id="d0c06-145">**Automatically install the redistributable prerequisites from the web** : Default.</span></span> <span data-ttu-id="d0c06-146">需要存取網際網路。</span><span class="sxs-lookup"><span data-stu-id="d0c06-146">Requires internet access.</span></span>
9. <span data-ttu-id="d0c06-147">**下載必要的可轉散發套件封包檔**：下載封包檔，以便稍後安裝。</span><span class="sxs-lookup"><span data-stu-id="d0c06-147">**Download the redistributable prerequisites CAB file** : Downloads a CAB file, which you can install later.</span></span>
10. <span data-ttu-id="d0c06-148">**從封包檔自動安裝必要的可轉散發套件**：如果您已下載封包檔，即可選取此選項來使用這些封包檔。</span><span class="sxs-lookup"><span data-stu-id="d0c06-148">**Automatically install the redistributable prerequisites from a CAB file**: If you previously downloaded the CAB files, you can select this option to use those CAB files.</span></span> 

    <span data-ttu-id="d0c06-149">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="d0c06-149">Select **Next**.</span></span>
  
11. <span data-ttu-id="d0c06-150">檢閱摘要頁面。</span><span class="sxs-lookup"><span data-stu-id="d0c06-150">Review the summary page.</span></span> <span data-ttu-id="d0c06-151">若要進行任何變更，請選取 [上一步] 以選取或取消選取任何元件。</span><span class="sxs-lookup"><span data-stu-id="d0c06-151">To make any changes, select **Back** to check or uncheck any components.</span></span> 

      <span data-ttu-id="d0c06-152">若要啟用在系統重新開機之後自動登入的功能，請選取 [設定] 並輸入登入資訊。</span><span class="sxs-lookup"><span data-stu-id="d0c06-152">To enable auto-logon after a system reboot, select **Set**, and enter the sign-in account.</span></span> <span data-ttu-id="d0c06-153">這只會在 BizTalk 安裝期間啟用。</span><span class="sxs-lookup"><span data-stu-id="d0c06-153">This is only enabled during the BizTalk setup.</span></span> <span data-ttu-id="d0c06-154">安裝程式完成時，即會停用此設定。</span><span class="sxs-lookup"><span data-stu-id="d0c06-154">When setup is complete, this setting is disabled.</span></span> 

     <span data-ttu-id="d0c06-155">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="d0c06-155">Select **Install**.</span></span>
  
12. <span data-ttu-id="d0c06-156">若要立即設定 BizTalk，請選取 [啟動 BizTalk Server 組態]。</span><span class="sxs-lookup"><span data-stu-id="d0c06-156">To configure BizTalk now, check **Launch BizTalk Server Configuration**.</span></span> <span data-ttu-id="d0c06-157">如果您不想立即設定 BizTalk，請取消選取這個選項，並選取 [完成] 以關閉安裝精靈。</span><span class="sxs-lookup"><span data-stu-id="d0c06-157">If you don't want to configure BizTalk now, then uncheck this option, and select **Finish** to close the installation wizard.</span></span> 

<span data-ttu-id="d0c06-158">暫存資料夾中即會產生安裝程式記錄檔，其類似於 `C:\Users\*username*\AppData\Local\Setup(011217 xxxxxx).htm`</span><span class="sxs-lookup"><span data-stu-id="d0c06-158">A setup log file is generated in a temp folder, similar to: `C:\Users\*username*\AppData\Local\Setup(011217 xxxxxx).htm`</span></span>
  
## <a name="check-the-installation"></a><span data-ttu-id="d0c06-159">檢查安裝</span><span class="sxs-lookup"><span data-stu-id="d0c06-159">Check the installation</span></span>

* <span data-ttu-id="d0c06-160">[程式和功能] 中應列出 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="d0c06-160">BizTalk Server is listed in **Programs and Features**.</span></span>
* <span data-ttu-id="d0c06-161">`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0` 登錄機碼應列出 BizTalk Server 的版本、安裝路徑、版本號碼和其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d0c06-161">The `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0` registry key lists the BizTalk Server version, the install path, the edition, and other details.</span></span>
* <span data-ttu-id="d0c06-162">您的應用程式中應列出 BizTalk Server 管理、組態和其他元件。</span><span class="sxs-lookup"><span data-stu-id="d0c06-162">BizTalk Server Administration, Configuration, and other components are listed in your Apps.</span></span> 

## <a name="next-step"></a><span data-ttu-id="d0c06-163">下一步</span><span class="sxs-lookup"><span data-stu-id="d0c06-163">Next step</span></span>
[<span data-ttu-id="d0c06-164">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d0c06-164">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)
---
title: "安裝 WCF LOB Adapter SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41b9b34b-3fbb-480f-a335-a218eab33693
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e9d4dfe5818e28e1ccd73b077c19c9d45ecb8cc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="174ec-102">安裝 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="174ec-102">Install the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="174ec-103">安裝和設定[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="174ec-103">Install and configure the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="174ec-104">需求</span><span class="sxs-lookup"><span data-stu-id="174ec-104">Requirements</span></span> 
<span data-ttu-id="174ec-105">安裝下列元件安裝在系統上[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="174ec-105">Install following components on the system where you install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> 

> [!NOTE]
> <span data-ttu-id="174ec-106">**如需支援版本的清單**，請參閱：</span><span class="sxs-lookup"><span data-stu-id="174ec-106">**For a list of the supported versions**, see:</span></span> 
> 
> [<span data-ttu-id="174ec-107">BizTalk Server 2016 的硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="174ec-107">Hardware and Software Requirements for BizTalk Server 2016</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
> [<span data-ttu-id="174ec-108">BizTalk Server 2013 和 2013 R2 的硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="174ec-108">Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)
 
 | | | 
 | --- | --- |
 | <span data-ttu-id="174ec-109">Windows</span><span class="sxs-lookup"><span data-stu-id="174ec-109">Windows</span></span> | <span data-ttu-id="174ec-110">x86 或 x64</span><span class="sxs-lookup"><span data-stu-id="174ec-110">x86 or x64</span></span> <br/><br/><span data-ttu-id="174ec-111">必要的作業系統資源包括：</span><span class="sxs-lookup"><span data-stu-id="174ec-111">Required OS resources include:</span></span><br/> <ul><li><span data-ttu-id="174ec-112">支援 OleTx 交易時所需的 Microsoft Distributed Transaction Coordinator (MSDTC):</span><span class="sxs-lookup"><span data-stu-id="174ec-112">Microsoft Distributed Transaction Coordinator (MSDTC) : Required to support OleTx transactions</span></span></li><li><span data-ttu-id="174ec-113">支援可信賴傳訊所需的訊息佇列 (MSMQ):</span><span class="sxs-lookup"><span data-stu-id="174ec-113">Message Queuing (MSMQ) : Required to support reliable messaging</span></span></li><li><span data-ttu-id="174ec-114">如果您想要裝載在 IIS 中的應用程式所需的 Internet Information Services (IIS):</span><span class="sxs-lookup"><span data-stu-id="174ec-114">Internet Information Services (IIS) : Required if you want to host your application in IIS</span></span></li><li><span data-ttu-id="174ec-115">如果您想要裝載 WAS 中的應用程式所需的 Windows Process Activation Service (WAS):</span><span class="sxs-lookup"><span data-stu-id="174ec-115">Windows Process Activation Service (WAS) : Required if you want to host your application in WAS</span></span></li></ul> |
 |<span data-ttu-id="174ec-116">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="174ec-116">Windows Communication Foundation</span></span>| | 
 | [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)] | | 
 | [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] | <span data-ttu-id="174ec-117">如果您要建置自訂的配接器，或開發使用配接器的方案建置所需[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="174ec-117">Required if you are building custom adapters, or developing solutions that use the adapters built with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> |
| [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] | <span data-ttu-id="174ec-118">如果您使用與配接器所需[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="174ec-118">Required if you use the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  |


  
## <a name="install"></a><span data-ttu-id="174ec-119">Install</span><span class="sxs-lookup"><span data-stu-id="174ec-119">Install</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="174ec-120">關閉所有 Visual Studio 執行個體</span><span class="sxs-lookup"><span data-stu-id="174ec-120">Close all instances of Visual Studio</span></span>
> * <span data-ttu-id="174ec-121">若要執行**完成**安裝程式，確認已在電腦上安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="174ec-121">To do a **Complete** setup, confirm that BizTalk Server is installed on the computer.</span></span>  
  
1.  <span data-ttu-id="174ec-122">執行[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe**以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="174ec-122">Run the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe** as Administrator.</span></span>
  
2.  <span data-ttu-id="174ec-123">選取**安裝 Microsoft BizTalk Adapters**，然後選取**安裝 Microsoft WCF LOB 配接器 SDK**。</span><span class="sxs-lookup"><span data-stu-id="174ec-123">Select **Install Microsoft BizTalk Adapters**, and then select **Install Microsoft WCF LOB Adapter SDK**.</span></span>  
  
3.  <span data-ttu-id="174ec-124">在**歡迎**畫面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="174ec-124">On the **Welcome** screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="174ec-125">接受授權合約，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="174ec-125">Accept the license agreement, and select **Next**.</span></span>  
  
5.  <span data-ttu-id="174ec-126">在**選擇安裝類型**，選取安裝類型：</span><span class="sxs-lookup"><span data-stu-id="174ec-126">In **Choose Setup Type**, select the type of installation:</span></span>  
  
    -   <span data-ttu-id="174ec-127">若要安裝的通用執行的階段和工具，請選取**一般**。</span><span class="sxs-lookup"><span data-stu-id="174ec-127">To install the common run time and tools, select **Typical**.</span></span>  
  
    -   <span data-ttu-id="174ec-128">若要選取您想要安裝的安裝位置的功能，請選取**自訂**，然後選取您想要安裝的功能。</span><span class="sxs-lookup"><span data-stu-id="174ec-128">To select the features that you want to install and the installation location, select **Custom**, and then select the features you want to install.</span></span>  
  
    -   <span data-ttu-id="174ec-129">若要安裝所有功能，請選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="174ec-129">To install all the features, select **Complete**.</span></span>  
  
6.  <span data-ttu-id="174ec-130">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="174ec-130">Select **Install**.</span></span>  
  
## <a name="update-or-remove"></a><span data-ttu-id="174ec-131">更新或移除</span><span class="sxs-lookup"><span data-stu-id="174ec-131">Update or remove</span></span>
  
1.  <span data-ttu-id="174ec-132">開啟**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="174ec-132">Open **Programs and Feature**.</span></span> 
  
2.  <span data-ttu-id="174ec-133">在清單中，選取**Windows Communication Foundation LOB 配接器 SDK**，然後選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="174ec-133">In the list, select **Windows Communication Foundation LOB Adapter SDK**, and then select **Change**.</span></span>  
  
3.  <span data-ttu-id="174ec-134">在**歡迎**畫面上，選取**下一步**。</span><span class="sxs-lookup"><span data-stu-id="174ec-134">On the **Welcome** screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="174ec-135">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="174ec-135">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="174ec-136">若要選取您想要安裝的元件，請選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="174ec-136">To select the components that you want to install, select **Change**.</span></span>  
  
    -   <span data-ttu-id="174ec-137">若要修復最近安裝中的錯誤，請選取**修復**。</span><span class="sxs-lookup"><span data-stu-id="174ec-137">To repair errors in the most recent installation, select **Repair**.</span></span>  
  
    -   <span data-ttu-id="174ec-138">若要移除[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]從電腦中，選取**移除**。</span><span class="sxs-lookup"><span data-stu-id="174ec-138">To remove the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] from the computer, select **Remove**.</span></span>  
  
5.  <span data-ttu-id="174ec-139">如果您選擇修改安裝：</span><span class="sxs-lookup"><span data-stu-id="174ec-139">If you choose to modify the installation:</span></span>  
  
    1.  <span data-ttu-id="174ec-140">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="174ec-140">Select **Next**.</span></span>  
  
    2.  <span data-ttu-id="174ec-141">選取**變更**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="174ec-141">Select **Change**, and then select **Finish**.</span></span>  
  
6.  <span data-ttu-id="174ec-142">如果您選擇修復安裝，在**準備好修復 WCF LOB 配接器 SDK**對話方塊中，選取**修復**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="174ec-142">If you choose to repair the installation, in the **Ready to repair WCF LOB Adapter SDK** dialog box, select **Repair**, and then select **Finish**.</span></span>  
  
7.  <span data-ttu-id="174ec-143">如果您選擇在移除介面卡，**準備好要移除 WCF LOB 配接器 SDK**對話方塊中，選取**移除**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="174ec-143">If you choose to remove the adapters, in the **Ready to remove WCF LOB Adapter SDK** dialog box, select **Remove**, and then select **Finish**.</span></span>  
  
  
#### <a name="remove-custom-adapters-after-uninstalling-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="174ec-144">解除安裝 WCF LOB 配接器 SDK 之後移除自訂配接器</span><span class="sxs-lookup"><span data-stu-id="174ec-144">Remove custom adapters after uninstalling the WCF LOB Adapter SDK</span></span>  

 <span data-ttu-id="174ec-145">如果您已經開發使用任何自訂配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，而且您已在電腦上註冊這些配接器，您還必須完成下列程序。</span><span class="sxs-lookup"><span data-stu-id="174ec-145">If you have developed any custom adapters using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and you have registered these adapters on your computer, you must also complete the following procedure.</span></span>  
  
1.  <span data-ttu-id="174ec-146">從全域組件快取 (GAC) 移除自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="174ec-146">Remove the custom adapter from the global assembly cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="174ec-147">開啟**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="174ec-147">Open a **Visual Studio command prompt**.</span></span>  
  
    2.  <span data-ttu-id="174ec-148">移除自訂**配接器.dll**從 GAC 使用**命令 gacutil /u**。</span><span class="sxs-lookup"><span data-stu-id="174ec-148">Remove the custom **adapter .dll** from the GAC using **command gacutil /u**.</span></span>  
  
2.  <span data-ttu-id="174ec-149">移除 machine.config 中的自訂配接器繫結的參考</span><span class="sxs-lookup"><span data-stu-id="174ec-149">Remove the references to the custom adapter binding from machine.config</span></span>  
  
    1.  <span data-ttu-id="174ec-150">移至下的 machine.config 檔案\<*系統磁碟機*\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="174ec-150">Go to the machine.config file under \<*system drive*\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    2.  <span data-ttu-id="174ec-151">使用文字編輯器開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="174ec-151">Open the file by using a text editor.</span></span>  
  
    3.  <span data-ttu-id="174ec-152">搜尋的項目 bindingExtensions、 用戶端及 bindingElementExtensions system.serviceModel\extensions 底下。</span><span class="sxs-lookup"><span data-stu-id="174ec-152">Search for the element bindingExtensions, client and bindingElementExtensions under system.serviceModel\extensions.</span></span>  
  
    4.  <span data-ttu-id="174ec-153">移除屬於自訂配接器的 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="174ec-153">Remove the WCF binding that pertains to your custom adapter.</span></span>  
  
## <a name="do-a-silent-installation"></a><span data-ttu-id="174ec-154">執行無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="174ec-154">Do a silent installation</span></span>  
 <span data-ttu-id="174ec-155">無訊息安裝適合的測試案例或大型企業部署的一部分。</span><span class="sxs-lookup"><span data-stu-id="174ec-155">A silent installation is ideal for test scenarios or as part of a large-scale enterprise deployment.</span></span> [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<span data-ttu-id="174ec-156">提供命令列參數，您可以搭配 AdapterFramework.msi 執行無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="174ec-156"> provides command line parameters that you can use with AdapterFramework.msi to perform a silent installation.</span></span>  
 
> [!NOTE]
>  <span data-ttu-id="174ec-157">若要執行無訊息安裝，您應該在電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="174ec-157">To perform silent installation, you should be an Administrator on the computer.</span></span> 

  
1.  <span data-ttu-id="174ec-158">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="174ec-158">Open a command prompt as administrator.</span></span>  
  
2.  <span data-ttu-id="174ec-159">輸入以下內容：</span><span class="sxs-lookup"><span data-stu-id="174ec-159">Type the following:</span></span>
  
    ```  
    AdapterFramework.msi /quiet MUOPTIN=”Yes”  
    ```  
  
    <span data-ttu-id="174ec-160">AdapterFramework.msi 搭配使用下列命令列選項：</span><span class="sxs-lookup"><span data-stu-id="174ec-160">Use the following command line options in conjunction with AdapterFramework.msi:</span></span>  
  
    * <span data-ttu-id="174ec-161">使用`/quiet`安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]以無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="174ec-161">Use `/quiet` to install [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] silently.</span></span>  
  
    * <span data-ttu-id="174ec-162">使用 MUOPTIN ="Yes"&#124;"No"，表示如果[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]應該檢查更新檔與 Microsoft Update。</span><span class="sxs-lookup"><span data-stu-id="174ec-162">Use MUOPTIN=”Yes”&#124;”No” to indicate if the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] should check for updates with Microsoft Update.</span></span>  
    
        <span data-ttu-id="174ec-163">當設定為 [是]，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]檢查透過 Microsoft Update 的更新。</span><span class="sxs-lookup"><span data-stu-id="174ec-163">When set to Yes, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] checks for updates through Microsoft Update.</span></span> <span data-ttu-id="174ec-164">當設定為 否[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不會檢查更新與 Microsoft Update。</span><span class="sxs-lookup"><span data-stu-id="174ec-164">When set to no [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not check for updates with Microsoft Update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="174ec-165">若要顯示的命令列安裝的其他選項，請輸入`AdapterFramework.msi /?`在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="174ec-165">To display additional options for command line installation, type `AdapterFramework.msi /?`at the command prompt.</span></span>  
  

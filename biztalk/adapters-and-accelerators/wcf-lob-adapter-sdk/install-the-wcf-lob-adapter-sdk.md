---
title: 安裝 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41b9b34b-3fbb-480f-a335-a218eab33693
caps.latest.revision: 40
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95fba9830bd97dd619cd16d18c0363a4525d1397
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999703"
---
# <a name="install-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="dc470-102">安裝 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="dc470-102">Install the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="dc470-103">安裝和設定[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dc470-103">Install and configure the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> 

## <a name="requirements"></a><span data-ttu-id="dc470-104">需求</span><span class="sxs-lookup"><span data-stu-id="dc470-104">Requirements</span></span> 
<span data-ttu-id="dc470-105">安裝下列元件安裝在系統上[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dc470-105">Install following components on the system where you install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> 

> [!NOTE]
> <span data-ttu-id="dc470-106">**如需支援版本的清單**，請參閱：</span><span class="sxs-lookup"><span data-stu-id="dc470-106">**For a list of the supported versions**, see:</span></span> 
> 
> [<span data-ttu-id="dc470-107">BizTalk Server 2016 的硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="dc470-107">Hardware and Software Requirements for BizTalk Server 2016</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
> [<span data-ttu-id="dc470-108">BizTalk Server 2013 和 2013 R2 的硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="dc470-108">Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)

|                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                         <span data-ttu-id="dc470-109">Windows</span><span class="sxs-lookup"><span data-stu-id="dc470-109">Windows</span></span>                                          | <span data-ttu-id="dc470-110">x86 或 x64</span><span class="sxs-lookup"><span data-stu-id="dc470-110">x86 or x64</span></span> <br/><br/><span data-ttu-id="dc470-111">所需的 OS 資源包括：</span><span class="sxs-lookup"><span data-stu-id="dc470-111">Required OS resources include:</span></span><br/> <ul><li><span data-ttu-id="dc470-112">支援 OleTx 異動時所需的 Microsoft Distributed Transaction Coordinator (MSDTC):</span><span class="sxs-lookup"><span data-stu-id="dc470-112">Microsoft Distributed Transaction Coordinator (MSDTC) : Required to support OleTx transactions</span></span></li><li><span data-ttu-id="dc470-113">支援可靠傳訊所需的訊息佇列 (MSMQ):</span><span class="sxs-lookup"><span data-stu-id="dc470-113">Message Queuing (MSMQ) : Required to support reliable messaging</span></span></li><li><span data-ttu-id="dc470-114">如果您想要裝載在 IIS 中的應用程式所需的 Internet Information Services (IIS):</span><span class="sxs-lookup"><span data-stu-id="dc470-114">Internet Information Services (IIS) : Required if you want to host your application in IIS</span></span></li><li><span data-ttu-id="dc470-115">如果您想要裝載在 WAS 中的應用程式所需的 Windows Process Activation Service (WAS):</span><span class="sxs-lookup"><span data-stu-id="dc470-115">Windows Process Activation Service (WAS) : Required if you want to host your application in WAS</span></span></li></ul> |
|                             <span data-ttu-id="dc470-116">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="dc470-116">Windows Communication Foundation</span></span>                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|        [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]        |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|       [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]       |                                                                                                                                     <span data-ttu-id="dc470-117">如果您正在建置自訂的配接器，或開發使用配接器的方案建置所需[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dc470-117">Required if you are building custom adapters, or developing solutions that use the adapters built with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>                                                                                                                                      |
| [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] |                                                                                                                                                                 <span data-ttu-id="dc470-118">如果您使用與配接器所需[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dc470-118">Required if you use the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>                                                                                                                                                                 |

## <a name="install"></a><span data-ttu-id="dc470-119">安裝</span><span class="sxs-lookup"><span data-stu-id="dc470-119">Install</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="dc470-120">關閉所有 Visual Studio 執行個體</span><span class="sxs-lookup"><span data-stu-id="dc470-120">Close all instances of Visual Studio</span></span>
> * <span data-ttu-id="dc470-121">若要執行**完成**安裝程式，確認已在電腦上安裝 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="dc470-121">To do a **Complete** setup, confirm that BizTalk Server is installed on the computer.</span></span>  

1. <span data-ttu-id="dc470-122">執行[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe**以系統管理員身分。</span><span class="sxs-lookup"><span data-stu-id="dc470-122">Run the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe** as Administrator.</span></span>

2. <span data-ttu-id="dc470-123">選取 **安裝 Microsoft BizTalk Adapters**，然後選取**安裝 Microsoft WCF LOB 配接器 SDK**。</span><span class="sxs-lookup"><span data-stu-id="dc470-123">Select **Install Microsoft BizTalk Adapters**, and then select **Install Microsoft WCF LOB Adapter SDK**.</span></span>  

3. <span data-ttu-id="dc470-124">在 [**歡迎**畫面上，選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="dc470-124">On the **Welcome** screen, select **Next**.</span></span>  

4. <span data-ttu-id="dc470-125">接受授權合約，然後選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="dc470-125">Accept the license agreement, and select **Next**.</span></span>  

5. <span data-ttu-id="dc470-126">在 **選擇 安裝類型**，選取安裝類型：</span><span class="sxs-lookup"><span data-stu-id="dc470-126">In **Choose Setup Type**, select the type of installation:</span></span>  

   -   <span data-ttu-id="dc470-127">若要安裝的通用執行的階段和工具，請選取**典型**。</span><span class="sxs-lookup"><span data-stu-id="dc470-127">To install the common run time and tools, select **Typical**.</span></span>  

   -   <span data-ttu-id="dc470-128">若要選取您想要安裝的安裝位置的功能，請選取**自訂**，然後選取您想要安裝的功能。</span><span class="sxs-lookup"><span data-stu-id="dc470-128">To select the features that you want to install and the installation location, select **Custom**, and then select the features you want to install.</span></span>  

   -   <span data-ttu-id="dc470-129">若要安裝所有功能，請選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="dc470-129">To install all the features, select **Complete**.</span></span>  

6. <span data-ttu-id="dc470-130">選取 [安裝]。</span><span class="sxs-lookup"><span data-stu-id="dc470-130">Select **Install**.</span></span>  

## <a name="update-or-remove"></a><span data-ttu-id="dc470-131">更新或移除</span><span class="sxs-lookup"><span data-stu-id="dc470-131">Update or remove</span></span>

1. <span data-ttu-id="dc470-132">開啟**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="dc470-132">Open **Programs and Feature**.</span></span> 

2. <span data-ttu-id="dc470-133">在清單中，選取**Windows Communication Foundation LOB 配接器 SDK**，然後選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="dc470-133">In the list, select **Windows Communication Foundation LOB Adapter SDK**, and then select **Change**.</span></span>  

3. <span data-ttu-id="dc470-134">在 [**歡迎**畫面上，選取**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="dc470-134">On the **Welcome** screen, select **Next**.</span></span>  

4. <span data-ttu-id="dc470-135">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="dc470-135">Do one of the following:</span></span>  

   - <span data-ttu-id="dc470-136">若要選取您想要安裝的元件，請選取**變更**。</span><span class="sxs-lookup"><span data-stu-id="dc470-136">To select the components that you want to install, select **Change**.</span></span>  

   - <span data-ttu-id="dc470-137">若要修復最近安裝中的錯誤，請選取**修復**。</span><span class="sxs-lookup"><span data-stu-id="dc470-137">To repair errors in the most recent installation, select **Repair**.</span></span>  

   - <span data-ttu-id="dc470-138">若要移除[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]從電腦中，選取**移除**。</span><span class="sxs-lookup"><span data-stu-id="dc470-138">To remove the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] from the computer, select **Remove**.</span></span>  

5. <span data-ttu-id="dc470-139">如果您選擇修改安裝：</span><span class="sxs-lookup"><span data-stu-id="dc470-139">If you choose to modify the installation:</span></span>  

   1.  <span data-ttu-id="dc470-140">選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="dc470-140">Select **Next**.</span></span>  

   2.  <span data-ttu-id="dc470-141">選取 **變更**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="dc470-141">Select **Change**, and then select **Finish**.</span></span>  

6. <span data-ttu-id="dc470-142">如果您選擇修復安裝，在**準備好修復 WCF LOB 配接器 SDK**對話方塊中，選取**修復**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="dc470-142">If you choose to repair the installation, in the **Ready to repair WCF LOB Adapter SDK** dialog box, select **Repair**, and then select **Finish**.</span></span>  

7. <span data-ttu-id="dc470-143">如果您選擇要移除介面卡，在**即可移除 WCF LOB 配接器 SDK**對話方塊中，選取**移除**，然後選取**完成**。</span><span class="sxs-lookup"><span data-stu-id="dc470-143">If you choose to remove the adapters, in the **Ready to remove WCF LOB Adapter SDK** dialog box, select **Remove**, and then select **Finish**.</span></span>  


#### <a name="remove-custom-adapters-after-uninstalling-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="dc470-144">移除自訂配接器之後解除安裝 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="dc470-144">Remove custom adapters after uninstalling the WCF LOB Adapter SDK</span></span>  

 <span data-ttu-id="dc470-145">如果您在開發的任何自訂的配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，而且您已在電腦上註冊這些配接器，您還必須完成下列程序。</span><span class="sxs-lookup"><span data-stu-id="dc470-145">If you have developed any custom adapters using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and you have registered these adapters on your computer, you must also complete the following procedure.</span></span>  

1.  <span data-ttu-id="dc470-146">從全域組件快取 (GAC) 中移除自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="dc470-146">Remove the custom adapter from the global assembly cache (GAC).</span></span>  

    1.  <span data-ttu-id="dc470-147">開啟**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="dc470-147">Open a **Visual Studio command prompt**.</span></span>  

    2.  <span data-ttu-id="dc470-148">移除自訂**配接器.dll**從 GAC using**命令 gacutil /u**。</span><span class="sxs-lookup"><span data-stu-id="dc470-148">Remove the custom **adapter .dll** from the GAC using **command gacutil /u**.</span></span>  

2.  <span data-ttu-id="dc470-149">移除 machine.config 中的自訂配接器繫結的參考</span><span class="sxs-lookup"><span data-stu-id="dc470-149">Remove the references to the custom adapter binding from machine.config</span></span>  

    1.  <span data-ttu-id="dc470-150">移至 machine.config 檔名\<*系統磁碟機*\>: \WINDOWS\Microsoft.NET\Framework\\< 版本\>\CONFIG。</span><span class="sxs-lookup"><span data-stu-id="dc470-150">Go to the machine.config file under \<*system drive*\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  

    2.  <span data-ttu-id="dc470-151">使用文字編輯器中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="dc470-151">Open the file by using a text editor.</span></span>  

    3.  <span data-ttu-id="dc470-152">搜尋項目 bindingExtensions、 用戶端和 bindingElementExtensions system.serviceModel\extensions 底下。</span><span class="sxs-lookup"><span data-stu-id="dc470-152">Search for the element bindingExtensions, client and bindingElementExtensions under system.serviceModel\extensions.</span></span>  

    4.  <span data-ttu-id="dc470-153">移除屬於您自訂的配接器的 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="dc470-153">Remove the WCF binding that pertains to your custom adapter.</span></span>  

## <a name="do-a-silent-installation"></a><span data-ttu-id="dc470-154">執行無訊息安裝</span><span class="sxs-lookup"><span data-stu-id="dc470-154">Do a silent installation</span></span>  
 <span data-ttu-id="dc470-155">無訊息安裝適合的測試案例或大型企業部署的一部分。</span><span class="sxs-lookup"><span data-stu-id="dc470-155">A silent installation is ideal for test scenarios or as part of a large-scale enterprise deployment.</span></span> [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<span data-ttu-id="dc470-156"> 提供命令列參數，您可以搭配 AdapterFramework.msi 執行無訊息安裝。</span><span class="sxs-lookup"><span data-stu-id="dc470-156"> provides command line parameters that you can use with AdapterFramework.msi to perform a silent installation.</span></span>  

> [!NOTE]
>  <span data-ttu-id="dc470-157">若要執行無訊息安裝，您應該在電腦上的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="dc470-157">To perform silent installation, you should be an Administrator on the computer.</span></span> 


1. <span data-ttu-id="dc470-158">以系統管理員身分開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dc470-158">Open a command prompt as administrator.</span></span>  

2. <span data-ttu-id="dc470-159">輸入以下內容：</span><span class="sxs-lookup"><span data-stu-id="dc470-159">Type the following:</span></span>

   ```  
   AdapterFramework.msi /quiet MUOPTIN=”Yes”  
   ```  

   <span data-ttu-id="dc470-160">AdapterFramework.msi 搭配使用下列命令列選項：</span><span class="sxs-lookup"><span data-stu-id="dc470-160">Use the following command line options in conjunction with AdapterFramework.msi:</span></span>  

   * <span data-ttu-id="dc470-161">使用`/quiet`安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]以無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="dc470-161">Use `/quiet` to install [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] silently.</span></span>  

   * <span data-ttu-id="dc470-162">使用 MUOPTIN=[0|1 = [是]&#124;[否]，來指示是否[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]應該檢查 Microsoft update 的更新。</span><span class="sxs-lookup"><span data-stu-id="dc470-162">Use MUOPTIN=”Yes”&#124;”No” to indicate if the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] should check for updates with Microsoft Update.</span></span>  

       <span data-ttu-id="dc470-163">當設定為 [是]，[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]檢查透過 Microsoft Update 的更新。</span><span class="sxs-lookup"><span data-stu-id="dc470-163">When set to Yes, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] checks for updates through Microsoft Update.</span></span> <span data-ttu-id="dc470-164">若設為 no[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不會檢查 Microsoft update 的更新。</span><span class="sxs-lookup"><span data-stu-id="dc470-164">When set to no [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not check for updates with Microsoft Update.</span></span>  

> [!NOTE]
>  <span data-ttu-id="dc470-165">若要顯示的命令列安裝的其他選項，請輸入`AdapterFramework.msi /?`在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="dc470-165">To display additional options for command line installation, type `AdapterFramework.msi /?`at the command prompt.</span></span>  


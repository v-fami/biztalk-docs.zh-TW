---
title: 分析的追蹤工具的 MQSeries 配接器錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, about Adapter Trace Utility
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- errors, MQSeries adapters
- MQSeries adapters, Adapter Trace Utility
- Adapter Trace Utility, running
- MQSeries adapters, errors
- Adapter Trace Utility
ms.assetid: fdc73d99-3b73-491d-9b2f-7064364fefa7
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b53d1d2c0bbe19c54804b553041f8dc9ae4db20c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "26006624"
---
# <a name="analyzing-mqseries-adapter-errors-with-the-trace-tools"></a><span data-ttu-id="f9edc-102">使用追蹤工具分析 MQSeries 配接器錯誤</span><span class="sxs-lookup"><span data-stu-id="f9edc-102">Analyzing MQSeries Adapter Errors with the Trace Tools</span></span>
<span data-ttu-id="f9edc-103">您可以使用追蹤工具來分析執行應用程式時的傳訊失敗。</span><span class="sxs-lookup"><span data-stu-id="f9edc-103">You use the trace tools to analyze messaging failures when you run your application.</span></span> <span data-ttu-id="f9edc-104">透過 MQSeries 配接器，您必須使用兩個工具，一個是供配接器及您的 BizTalk 應用程式使用的工具 (trace.cmd)，另一個則是供 MQSAgent 使用的工具 (MQSTrace.cmd)。</span><span class="sxs-lookup"><span data-stu-id="f9edc-104">With the MQSeries adapter you must use two tools, one for the adapter and your BizTalk application (trace.cmd), and the other for the MQSAgent (MQSTrace.cmd).</span></span> <span data-ttu-id="f9edc-105">這兩種工具都會使用 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="f9edc-105">Both tools use tracelog.exe.</span></span> <span data-ttu-id="f9edc-106">如果尚未安裝 tracelog.exe，您就必須安裝該檔案。</span><span class="sxs-lookup"><span data-stu-id="f9edc-106">You have to install tracelog.exe if you do not already have it.</span></span>  
  
 <span data-ttu-id="f9edc-107">使用 trace.cmd 與 MQSTrace.cmd，您必須設定一個選項 (**-工具**)，因此這些工具可以找到 tracelog.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9edc-107">With both trace.cmd and MQSTrace.cmd you have to set an option (**-tools**) so that these tools can find the tracelog.exe file.</span></span>  
  
## <a name="install-the-trace-utility"></a><span data-ttu-id="f9edc-108">安裝追蹤公用程式</span><span class="sxs-lookup"><span data-stu-id="f9edc-108">Install the Trace Utility</span></span>  
 <span data-ttu-id="f9edc-109">若要安裝「BizTalk 配接器追蹤公用程式」，請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f9edc-109">To install the BizTalk Adapter Trace Utility, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f9edc-110">若要下載 Tracelog.exe 檔案，請瀏覽 Microsoft Platform SDK 下載網站，網址[ http://go.microsoft.com/fwlink/?LinkId=21975 ](http://go.microsoft.com/fwlink/?LinkId=21975)。</span><span class="sxs-lookup"><span data-stu-id="f9edc-110">To download the Tracelog.exe file, visit the Microsoft Platform SDK download Web site at [http://go.microsoft.com/fwlink/?LinkId=21975](http://go.microsoft.com/fwlink/?LinkId=21975).</span></span>  
  
2.  <span data-ttu-id="f9edc-111">按一下連結來啟動 Platform SDK Web 安裝程式 **x86.exe** 底部的 [Web] 頁面的檔案。</span><span class="sxs-lookup"><span data-stu-id="f9edc-111">Start the Platform SDK Web installation program by clicking the link for the **PSDK-x86.exe** file at the bottom of the Web page.</span></span>  
  
3.  <span data-ttu-id="f9edc-112">當提示出現時，請選擇自訂安裝選項。</span><span class="sxs-lookup"><span data-stu-id="f9edc-112">When you are prompted, choose the option for a custom installation.</span></span>  
  
4.  <span data-ttu-id="f9edc-113">在 **[自訂安裝]** 對話方塊中，按一下以清除所有可用的功能。</span><span class="sxs-lookup"><span data-stu-id="f9edc-113">In the **Custom Installation** dialog box, click to clear all the available features.</span></span>  
  
5.  <span data-ttu-id="f9edc-114">展開 **[Microsoft Windows Core SDK]** 功能，然後展開 **[工具]** 功能。</span><span class="sxs-lookup"><span data-stu-id="f9edc-114">Expand the **Microsoft Windows Core SDK** feature, and then expand the **Tools** feature.</span></span>  
  
6.  <span data-ttu-id="f9edc-115">選擇 **[工具 (Intel 64 位元)]** 功能，然後按一下 **[將會安裝至本機硬碟]**。</span><span class="sxs-lookup"><span data-stu-id="f9edc-115">Choose the **Tools (Intel 64-bit)** feature, and then click **Will be installed on local hard drive**.</span></span>  
  
7.  <span data-ttu-id="f9edc-116">按 **[下一步]**，然後再按 **[下一步]** ，以開始安裝。</span><span class="sxs-lookup"><span data-stu-id="f9edc-116">Click **Next**, and then click **Next** again to start the installation.</span></span>  
  
8.  <span data-ttu-id="f9edc-117">找出 *機*:\\*MicrosoftPlatformSDKInstallationFolder\bin* 資料夾，然後再將複製到 Microsoft BizTalk Server 安裝資料夾 Tracelog.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9edc-117">Locate the *drive*:\\*MicrosoftPlatformSDKInstallationFolder\bin* folder, and then copy the Tracelog.exe file to the Microsoft BizTalk Server installation folder.</span></span> <span data-ttu-id="f9edc-118">BizTalk Server 安裝資料夾也包含 Trace.cmd 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9edc-118">The BizTalk Server installation folder also contains the Trace.cmd file.</span></span>  
  
## <a name="enable-the-trace-utility"></a><span data-ttu-id="f9edc-119">啟用追蹤公用程式</span><span class="sxs-lookup"><span data-stu-id="f9edc-119">Enable the Trace Utility</span></span>  
 <span data-ttu-id="f9edc-120">若要啟用 BizTalk Server 中的「BizTalk 配接器追蹤公用程式」，請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f9edc-120">To enable the BizTalk Adapter Trace Utility in BizTalk Server, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f9edc-121">移到包含 trace.cmd 的目錄。</span><span class="sxs-lookup"><span data-stu-id="f9edc-121">Move to the directory that contains trace.cmd.</span></span> <span data-ttu-id="f9edc-122">預設位置是 Microsoft BizTalk Server 目錄。</span><span class="sxs-lookup"><span data-stu-id="f9edc-122">The default location is the Microsoft BizTalk Server directory.</span></span>  
  
2.  <span data-ttu-id="f9edc-123">輸入下列命令，並將括號括住的目錄以您電腦上包含 tracelog.exe 檔案的目錄替代，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="f9edc-123">Type the following command, substituting the directory that contains the tracelog.exe file on your computer for the directory in quotes, and then press ENTER:</span></span>  
  
     <span data-ttu-id="f9edc-124">**trace-tools"c:\Program Files\Microsoft SDK\Bin"**</span><span class="sxs-lookup"><span data-stu-id="f9edc-124">**trace -tools "c:\Program Files\Microsoft SDK\Bin"**</span></span>  
  
3.  <span data-ttu-id="f9edc-125">移到包含 MQSTrace.cmd 的目錄。</span><span class="sxs-lookup"><span data-stu-id="f9edc-125">Move to the directory that contains MQSTrace.cmd.</span></span>  
  
4.  <span data-ttu-id="f9edc-126">輸入下列命令，並將括號括住的目錄以您電腦上包含 tracelog.exe 檔案的目錄替代，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="f9edc-126">Type the following command, substituting the directory that contains the tracelog.exe file on your computer for the directory in quotes, and then press ENTER:</span></span>  
  
     <span data-ttu-id="f9edc-127">**MQSTrace-tools"c:\Program Files\Microsoft SDK\Bin 」**</span><span class="sxs-lookup"><span data-stu-id="f9edc-127">**MQSTrace -tools "c:\Program Files\Microsoft SDK\Bin"**</span></span>  
  
## <a name="run-the-trace-utility"></a><span data-ttu-id="f9edc-128">執行追蹤公用程式</span><span class="sxs-lookup"><span data-stu-id="f9edc-128">Run the Trace Utility</span></span>  
 <span data-ttu-id="f9edc-129">若要執行「BizTalk 配接器追蹤公用程式」，請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f9edc-129">To run the BizTalk Adapter Trace Utility, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f9edc-130">在命令提示字元中，輸入 **trace.cmd-start-high**, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f9edc-130">At the command prompt, type **trace.cmd -start -high**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="f9edc-131">執行失敗的實例。</span><span class="sxs-lookup"><span data-stu-id="f9edc-131">Run your failure scenario.</span></span>  
  
3.  <span data-ttu-id="f9edc-132">在命令提示字元中，輸入 **trace.cmd-停止**, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f9edc-132">At the command prompt, type **trace.cmd -stop**, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="f9edc-133">bts2006.bin 檔案包含追蹤工具的輸出。</span><span class="sxs-lookup"><span data-stu-id="f9edc-133">The bts2006.bin file contains the output of the trace tool.</span></span> <span data-ttu-id="f9edc-134">請連絡 Microsoft 產品支援服務以取得分析。</span><span class="sxs-lookup"><span data-stu-id="f9edc-134">Contact Microsoft Product Support Services for analysis.</span></span> <span data-ttu-id="f9edc-135">如需詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=41645 ](http://go.microsoft.com/fwlink/?LinkId=41645)。</span><span class="sxs-lookup"><span data-stu-id="f9edc-135">For more information, see [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).</span></span>  
  
 <span data-ttu-id="f9edc-136">若要執行 MQSAgent 追蹤公用程式，請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f9edc-136">To run the MQSAgent Trace Utility, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f9edc-137">在命令提示字元中，輸入 **MQSTrace.cmd-start-high**, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="f9edc-137">At the command prompt, type **MQSTrace.cmd -start -high**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="f9edc-138">執行失敗的實例。</span><span class="sxs-lookup"><span data-stu-id="f9edc-138">Run your failure scenario.</span></span>  
  
3.  <span data-ttu-id="f9edc-139">在命令提示字元中，輸入 **MQSTrace.cmd-停止**。</span><span class="sxs-lookup"><span data-stu-id="f9edc-139">At the command prompt, type **MQSTrace.cmd -stop**.</span></span>  
  
4.  <span data-ttu-id="f9edc-140">MQSAdapterTrace.bin 檔案包含追蹤工具的輸出。</span><span class="sxs-lookup"><span data-stu-id="f9edc-140">The MQSAdapterTrace.bin file contains the output of the trace tool.</span></span> <span data-ttu-id="f9edc-141">請連絡 Microsoft 產品支援服務以取得分析。</span><span class="sxs-lookup"><span data-stu-id="f9edc-141">Contact Microsoft Product Support Services for analysis.</span></span> <span data-ttu-id="f9edc-142">如需詳細資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=41645 ](http://go.microsoft.com/fwlink/?LinkId=41645)。</span><span class="sxs-lookup"><span data-stu-id="f9edc-142">For more information see [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).</span></span>
---
title: "MllpSend 工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MllpSend tool
- MLLP-encoded messages, receive adapters
- MLLP-encoded messages, MllpSend tool
ms.assetid: b1723d52-4909-4543-8215-4f73802b6c4f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed9b666b019fe7dc415f28c0dd01522b728b149c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="mllpsend-tool"></a><span data-ttu-id="71dbb-102">MllpSend 工具</span><span class="sxs-lookup"><span data-stu-id="71dbb-102">MllpSend Tool</span></span>
<span data-ttu-id="71dbb-103">您可以使用 MllpSend 工具來傳送資料至 MLLP 的接收位置。</span><span class="sxs-lookup"><span data-stu-id="71dbb-103">You can use the MllpSend tool to send data to an MLLP receive location.</span></span>  
  
 <span data-ttu-id="71dbb-104">安裝此工具透過[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]自訂安裝程序。</span><span class="sxs-lookup"><span data-stu-id="71dbb-104">You install this tool through the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Custom installation procedure.</span></span> <span data-ttu-id="71dbb-105">如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程正常運作。</span><span class="sxs-lookup"><span data-stu-id="71dbb-105">If you performed a Typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="71dbb-106">在 [自訂安裝] 畫面中，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。</span><span class="sxs-lookup"><span data-stu-id="71dbb-106">At the Custom Setup screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="71dbb-107">如需詳細資訊，請參閱[執行自訂安裝](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692)。</span><span class="sxs-lookup"><span data-stu-id="71dbb-107">For more information, see [Performing a Custom Installation](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span></span>  
  
 <span data-ttu-id="71dbb-108">BTAHL7 安裝程式會安裝在此工具*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\MLLP 公用程式。</span><span class="sxs-lookup"><span data-stu-id="71dbb-108">BTAHL7 setup installs this tool in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities.</span></span>  
  
 <span data-ttu-id="71dbb-109">您使用此工具中的[端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)、 [Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)、[批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)，而[訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="71dbb-109">You use this tool in the [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), the [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), the [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md), and the [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span></span> <span data-ttu-id="71dbb-110">如果您已安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]透過預設安裝中，且尚未安裝 MLLP 的 Testtools （包括 MllpSend 和 MllpReceive），您不能測試您的教學課程結果。</span><span class="sxs-lookup"><span data-stu-id="71dbb-110">If you installed [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] through the default installation, and have not installed the MLLP Testtools (including MllpSend and MllpReceive), you will not be able to test your tutorial results.</span></span>  
  
## <a name="tool-usage"></a><span data-ttu-id="71dbb-111">工具使用方式</span><span class="sxs-lookup"><span data-stu-id="71dbb-111">Tool Usage</span></span>  
 <span data-ttu-id="71dbb-112">下列顯示您用來叫用這個命令列工具的語法：</span><span class="sxs-lookup"><span data-stu-id="71dbb-112">The following shows the syntax you use to invoke this command-line tool:</span></span>  
  
```  
mllpsend.exe [/?] [/I <IP>] [/P <PORT>] [/TWOWAY] [/REPEAT <n>] [/F <FILENAME> | "TEXT"] /SB nn /EB nn /CR nn  
```  
  
 <span data-ttu-id="71dbb-113">下表說明每一部分 MllpSend 工具使用的語法。</span><span class="sxs-lookup"><span data-stu-id="71dbb-113">The following table describes each part of the syntax the MllpSend tool uses.</span></span>  
  
|<span data-ttu-id="71dbb-114">語法</span><span class="sxs-lookup"><span data-stu-id="71dbb-114">Syntax</span></span>|<span data-ttu-id="71dbb-115">Description</span><span class="sxs-lookup"><span data-stu-id="71dbb-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="71dbb-116">**/?**</span><span class="sxs-lookup"><span data-stu-id="71dbb-116">**/?**</span></span>|<span data-ttu-id="71dbb-117">在命令提示字元 視窗中顯示說明。</span><span class="sxs-lookup"><span data-stu-id="71dbb-117">Displays Help in the Command Prompt window.</span></span>|  
|<span data-ttu-id="71dbb-118">**/I \<IP\>**</span><span class="sxs-lookup"><span data-stu-id="71dbb-118">**/I \<IP\>**</span></span>|<span data-ttu-id="71dbb-119">表示要傳送至的位址。</span><span class="sxs-lookup"><span data-stu-id="71dbb-119">Denotes the address to send to.</span></span> <span data-ttu-id="71dbb-120">預設值為 localhost。</span><span class="sxs-lookup"><span data-stu-id="71dbb-120">The default value is localhost.</span></span>|  
|<span data-ttu-id="71dbb-121">**/P\<連接埠\>**</span><span class="sxs-lookup"><span data-stu-id="71dbb-121">**/P \<PORT\>**</span></span>|<span data-ttu-id="71dbb-122">表示將傳送至連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="71dbb-122">Denotes the port number to send to.</span></span> <span data-ttu-id="71dbb-123">預設值是**11000**。</span><span class="sxs-lookup"><span data-stu-id="71dbb-123">The default value is **11000**.</span></span>|  
|<span data-ttu-id="71dbb-124">**/F**</span><span class="sxs-lookup"><span data-stu-id="71dbb-124">**/F**</span></span>|<span data-ttu-id="71dbb-125">傳送檔案的檔案名稱的內容。</span><span class="sxs-lookup"><span data-stu-id="71dbb-125">Sends content of the file FILENAME.</span></span>|  
|<span data-ttu-id="71dbb-126">**/ 重複\<n\>**</span><span class="sxs-lookup"><span data-stu-id="71dbb-126">**/REPEAT \<n\>**</span></span>|<span data-ttu-id="71dbb-127">會傳送相同訊息 *n* 時間。</span><span class="sxs-lookup"><span data-stu-id="71dbb-127">Sends the same message *n* times.</span></span> <span data-ttu-id="71dbb-128">包裝函式的字元將會套用至各個訊息。</span><span class="sxs-lookup"><span data-stu-id="71dbb-128">The wrapper characters will be applied to each message.</span></span>|  
|<span data-ttu-id="71dbb-129">**/ TWOWAY**</span><span class="sxs-lookup"><span data-stu-id="71dbb-129">**/TWOWAY**</span></span>|<span data-ttu-id="71dbb-130">寄件者會等候來自接收者的回應。</span><span class="sxs-lookup"><span data-stu-id="71dbb-130">The sender will wait for a response from the receiver.</span></span> <span data-ttu-id="71dbb-131">必須指定 SB 和 EB。</span><span class="sxs-lookup"><span data-stu-id="71dbb-131">SB and EB need to be specified.</span></span> <span data-ttu-id="71dbb-132">CR 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="71dbb-132">CR is optional.</span></span> <span data-ttu-id="71dbb-133">在 檔案模式中，回應會儲存在檔案的檔案。回應。</span><span class="sxs-lookup"><span data-stu-id="71dbb-133">In File mode, the response is stored in the file FILE.RESPONSE.</span></span>|  
|<span data-ttu-id="71dbb-134">**/SB**</span><span class="sxs-lookup"><span data-stu-id="71dbb-134">**/SB**</span></span>|<span data-ttu-id="71dbb-135">設定開始區塊分隔符號位元組的 ASCII 值。</span><span class="sxs-lookup"><span data-stu-id="71dbb-135">Sets the ASCII value of the Start Block Delimiter Byte.</span></span> <span data-ttu-id="71dbb-136">預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="71dbb-136">The default is none.</span></span>|  
|<span data-ttu-id="71dbb-137">**/EB**</span><span class="sxs-lookup"><span data-stu-id="71dbb-137">**/EB**</span></span>|<span data-ttu-id="71dbb-138">設定結束區塊分隔符號位元組的 ASCII 值。</span><span class="sxs-lookup"><span data-stu-id="71dbb-138">Sets the ASCII value of the End Block Delimiter Byte.</span></span> <span data-ttu-id="71dbb-139">預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="71dbb-139">The default is none.</span></span>|  
|<span data-ttu-id="71dbb-140">**/CR**</span><span class="sxs-lookup"><span data-stu-id="71dbb-140">**/CR**</span></span>|<span data-ttu-id="71dbb-141">設定的歸位字元傳回分隔符號位元組的 ASCII 值。</span><span class="sxs-lookup"><span data-stu-id="71dbb-141">Sets the ASCII value of the Carriage Return Delimiter Byte.</span></span> <span data-ttu-id="71dbb-142">預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="71dbb-142">The default is none.</span></span>|  
  
## <a name="examples-of-tool-use"></a><span data-ttu-id="71dbb-143">工具使用的範例</span><span class="sxs-lookup"><span data-stu-id="71dbb-143">Examples of Tool Use</span></span>  
 <span data-ttu-id="71dbb-144">下列範例會示範如何使用 MllpSend 工具。</span><span class="sxs-lookup"><span data-stu-id="71dbb-144">The following examples demonstrate how you can use the MllpSend tool.</span></span>  
  
 <span data-ttu-id="71dbb-145">**範例 1。**</span><span class="sxs-lookup"><span data-stu-id="71dbb-145">**Example 1.**</span></span> <span data-ttu-id="71dbb-146">您可以使用下列命令，將訊息傳送至單向介面卡接聽連接埠 13000"myserver"伺服器上。</span><span class="sxs-lookup"><span data-stu-id="71dbb-146">You can use the following command to send a message to a one-way adapter listening on port 13000 on server "myserver".</span></span> <span data-ttu-id="71dbb-147">包裝函式字元的 ASCII 值為 SB 11、 EB 28 和 CR 13。</span><span class="sxs-lookup"><span data-stu-id="71dbb-147">The ASCII values of the wrapper characters are SB 11, EB 28, and CR 13.</span></span>  
  
```  
mllpsend.exe /I myserver /P 13000 /SB 11 /EB 28 /CR 13 "A short message"  
```  
  
 <span data-ttu-id="71dbb-148">**範例 2。**</span><span class="sxs-lookup"><span data-stu-id="71dbb-148">**Example 2.**</span></span> <span data-ttu-id="71dbb-149">您可以使用下列命令，將訊息 100 次傳送至雙向介面卡上接聽連接埠 11000 server"localhost"。</span><span class="sxs-lookup"><span data-stu-id="71dbb-149">You can use the following command to send a message 100 times to a two-way adapter listening on port 11000 on server "localhost".</span></span> <span data-ttu-id="71dbb-150">包裝函式字元的 ASCII 值為 SB 11、 EB 28 和 CR 13。</span><span class="sxs-lookup"><span data-stu-id="71dbb-150">The ASCII values of the wrapper characters are SB 11, EB 28, and CR 13.</span></span>  
  
```  
mllpsend.exe /SB 11 /EB 28 /CR 13 /TWOWAY /REPEAT 100 "A short message"  
```  
  
## <a name="see-also"></a><span data-ttu-id="71dbb-151">請參閱</span><span class="sxs-lookup"><span data-stu-id="71dbb-151">See Also</span></span>  
 [<span data-ttu-id="71dbb-152">公用程式</span><span class="sxs-lookup"><span data-stu-id="71dbb-152">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)
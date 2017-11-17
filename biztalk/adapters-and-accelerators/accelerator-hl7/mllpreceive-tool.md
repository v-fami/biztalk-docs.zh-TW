---
title: "MllpReceive 工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, send adapters
- MllpReceive tool
- MLLP-encoded messages, MllpReceive tool
ms.assetid: 7069444b-1412-40bf-b567-fa86f76cd007
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c23aac352b47a328cfc8f412bb3beca50a61e1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mllpreceive-tool"></a><span data-ttu-id="a0734-102">MllpReceive 工具</span><span class="sxs-lookup"><span data-stu-id="a0734-102">MllpReceive Tool</span></span>
<span data-ttu-id="a0734-103">您可以使用 MllpReceive 工具從 MLLP 傳送連接埠接收資料。</span><span class="sxs-lookup"><span data-stu-id="a0734-103">You can use the MllpReceive tool to receive data from an MLLP send port.</span></span>  
  
 <span data-ttu-id="a0734-104">安裝此工具透過[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]自訂安裝程序。</span><span class="sxs-lookup"><span data-stu-id="a0734-104">You install this tool through the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Custom installation procedure.</span></span> <span data-ttu-id="a0734-105">如果您執行一般安裝 BTAHL7 安裝，然後您必須執行自訂安裝並測試工具安裝進行本教學課程正常運作。</span><span class="sxs-lookup"><span data-stu-id="a0734-105">If you performed a Typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="a0734-106">在 [自訂安裝] 畫面中，選取**MLLP 測試工具**從**配接器**資料夾，然後選取**測試執行個體**從**成品**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0734-106">At the Custom Setup screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="a0734-107">如需詳細資訊，請參閱[執行自訂安裝](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692)。</span><span class="sxs-lookup"><span data-stu-id="a0734-107">For more information, see [Performing a Custom Installation](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span></span>  
  
 <span data-ttu-id="a0734-108">BTAHL7 安裝程式會安裝在此工具*\<磁碟機 >*: \Program Files\Microsoft BizTalk\<版本 > Accelerator for HL7\SDK\MLLP 公用程式。</span><span class="sxs-lookup"><span data-stu-id="a0734-108">BTAHL7 setup installs this tool in *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\MLLP Utilities.</span></span>  
  
 <span data-ttu-id="a0734-109">您使用此工具中的[端對端教學課程](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)、 [Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)、[批次的教學課程](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)，而[訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a0734-109">You use this tool in the [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), the [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), the [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md), and the [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span></span> <span data-ttu-id="a0734-110">如果您已安裝[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]透過預設安裝中，且尚未安裝 MLLPTest 的工具 （包括 MllpReceive 和 MllpSend），您不能測試您的教學課程結果。</span><span class="sxs-lookup"><span data-stu-id="a0734-110">If you installed [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] through the default installation, and have not installed the MLLPTest tool (including MllpReceive and MllpSend), you will not be able to test your tutorial results.</span></span>  
  
## <a name="tool-usage"></a><span data-ttu-id="a0734-111">工具使用方式</span><span class="sxs-lookup"><span data-stu-id="a0734-111">Tool Usage</span></span>  
 <span data-ttu-id="a0734-112">下列顯示您用來叫用這個命令列工具的語法：</span><span class="sxs-lookup"><span data-stu-id="a0734-112">The following shows the syntax you use to invoke this command-line tool:</span></span>  
  
```  
mllpreceive.exe [/?] [/I <IP>] [/P <PORT>] [/SPLIT] [/D <DIRECTORY>] [/STATICACK "ACKTEXT" | /HL7ACK <FILENAME>] /SB nn /EB nn /CR nn  
```  
  
 <span data-ttu-id="a0734-113">下表說明每一部分 MllpReceive 工具使用的語法。</span><span class="sxs-lookup"><span data-stu-id="a0734-113">The following table describes each part of the syntax the MllpReceive tool uses.</span></span>  
  
|<span data-ttu-id="a0734-114">語法</span><span class="sxs-lookup"><span data-stu-id="a0734-114">Syntax</span></span>|<span data-ttu-id="a0734-115">意義</span><span class="sxs-lookup"><span data-stu-id="a0734-115">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="a0734-116">/?</span><span class="sxs-lookup"><span data-stu-id="a0734-116">/?</span></span>|<span data-ttu-id="a0734-117">顯示此說明。</span><span class="sxs-lookup"><span data-stu-id="a0734-117">Displays this help.</span></span>|  
|<span data-ttu-id="a0734-118">/I \<IP ></span><span class="sxs-lookup"><span data-stu-id="a0734-118">/I \<IP></span></span>|<span data-ttu-id="a0734-119">表示要接聽的位址。</span><span class="sxs-lookup"><span data-stu-id="a0734-119">Denotes the address to listen to.</span></span> <span data-ttu-id="a0734-120">預設為所有可用的 Ip。</span><span class="sxs-lookup"><span data-stu-id="a0734-120">The default is all available IPs.</span></span>|  
|<span data-ttu-id="a0734-121">/P\<連接埠 ></span><span class="sxs-lookup"><span data-stu-id="a0734-121">/P \<PORT></span></span>|<span data-ttu-id="a0734-122">表示要聆聽的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="a0734-122">Denotes the port number to listen to.</span></span> <span data-ttu-id="a0734-123">預設值是 12000。</span><span class="sxs-lookup"><span data-stu-id="a0734-123">The default value is 12000.</span></span>|  
|<span data-ttu-id="a0734-124">/D\<目錄 ></span><span class="sxs-lookup"><span data-stu-id="a0734-124">/D \<DIRECTORY></span></span>|<span data-ttu-id="a0734-125">將所有收到的訊息儲存在目錄中\<目錄 >。</span><span class="sxs-lookup"><span data-stu-id="a0734-125">Stores all received message(s) in the directory in \<DIRECTORY>.</span></span> <span data-ttu-id="a0734-126">如果您未指定\<目錄 >，預設目錄是 %TEMP%。</span><span class="sxs-lookup"><span data-stu-id="a0734-126">If you do not specify \<DIRECTORY>, the default directory is %TEMP%.</span></span>|  
|<span data-ttu-id="a0734-127">/ 分割</span><span class="sxs-lookup"><span data-stu-id="a0734-127">/SPLIT</span></span>|<span data-ttu-id="a0734-128">將已接收的資料分割成個別的分隔符號為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="a0734-128">Splits the received data into separate messages based on the delimiters.</span></span> <span data-ttu-id="a0734-129">需要 SB 和 EB。</span><span class="sxs-lookup"><span data-stu-id="a0734-129">SB and EB are required.</span></span> <span data-ttu-id="a0734-130">CR 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a0734-130">CR is optional.</span></span>|  
|<span data-ttu-id="a0734-131">/ STATICACK</span><span class="sxs-lookup"><span data-stu-id="a0734-131">/STATICACK</span></span>|<span data-ttu-id="a0734-132">靜態通知傳回給寄件者。</span><span class="sxs-lookup"><span data-stu-id="a0734-132">The static acknowledgment returned to the sender.</span></span> <span data-ttu-id="a0734-133">將會強制執行分隔模式。</span><span class="sxs-lookup"><span data-stu-id="a0734-133">Will enforce SPLIT mode.</span></span>|  
|<span data-ttu-id="a0734-134">/ HL7ACK</span><span class="sxs-lookup"><span data-stu-id="a0734-134">/HL7ACK</span></span>|<span data-ttu-id="a0734-135">HL7 通知傳回給寄件者。</span><span class="sxs-lookup"><span data-stu-id="a0734-135">The HL7 acknowledgment returned to the sender.</span></span> <span data-ttu-id="a0734-136">檔名表示包含 HL7 通知的檔案名稱</span><span class="sxs-lookup"><span data-stu-id="a0734-136">FILENAME denotes the name of the file containing the HL7 ACK.</span></span> <span data-ttu-id="a0734-137">將會強制執行分隔模式。</span><span class="sxs-lookup"><span data-stu-id="a0734-137">Will enforce SPLIT mode.</span></span>|  
|<span data-ttu-id="a0734-138">/SB</span><span class="sxs-lookup"><span data-stu-id="a0734-138">/SB</span></span>|<span data-ttu-id="a0734-139">設定開始區塊分隔符號位元組的 ASCII 值。</span><span class="sxs-lookup"><span data-stu-id="a0734-139">Sets the ASCII value of Start Block Delimiter Byte.</span></span> <span data-ttu-id="a0734-140">預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="a0734-140">The default is none.</span></span>|  
|<span data-ttu-id="a0734-141">/EB</span><span class="sxs-lookup"><span data-stu-id="a0734-141">/EB</span></span>|<span data-ttu-id="a0734-142">設定結束區塊分隔符號位元組的 ASCII 值。</span><span class="sxs-lookup"><span data-stu-id="a0734-142">Sets the ASCII value of End Block Delimiter Byte.</span></span> <span data-ttu-id="a0734-143">預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="a0734-143">The default is none.</span></span>|  
|<span data-ttu-id="a0734-144">/CR</span><span class="sxs-lookup"><span data-stu-id="a0734-144">/CR</span></span>|<span data-ttu-id="a0734-145">設定傳回分隔符號位元組的歸位字元的 ASCII 值。</span><span class="sxs-lookup"><span data-stu-id="a0734-145">Sets the ASCII value of Carriage Return Delimiter Byte.</span></span> <span data-ttu-id="a0734-146">預設值為 none。</span><span class="sxs-lookup"><span data-stu-id="a0734-146">The default is none.</span></span>|  
  
## <a name="example-of-tool-use"></a><span data-ttu-id="a0734-147">工具使用的範例</span><span class="sxs-lookup"><span data-stu-id="a0734-147">Example of Tool Use</span></span>  
 <span data-ttu-id="a0734-148">您可以為接聽通訊埠 10000 上 localhost，請使用下列命令，並儲存到不同的檔案在 C:\TEMP 的訊息：</span><span class="sxs-lookup"><span data-stu-id="a0734-148">You can use the following command to listen to port 10000 on localhost, and save messages to separate files on C:\TEMP:</span></span>  
  
```  
mllpreceive.exe /P 10000 /SPLIT /SB 11 /EB 28 /CR 13 /D C:\TEMP  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0734-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0734-149">See Also</span></span>  
 [<span data-ttu-id="a0734-150">公用程式</span><span class="sxs-lookup"><span data-stu-id="a0734-150">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)
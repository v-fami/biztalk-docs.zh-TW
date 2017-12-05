---
title: "FileTransport 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a32c8cbf-0c17-4237-b2a3-9d21faa13496
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38c08be5cd58ed6c80af351715ff6257f533c6af
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="filetransport-sample"></a><span data-ttu-id="a51c2-102">FileTransport 範例</span><span class="sxs-lookup"><span data-stu-id="a51c2-102">FileTransport Sample</span></span>
<span data-ttu-id="a51c2-103">FileTransport 範例會示範如何設定 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 使用檔案連接埠，而不是 SQL 連接埠。</span><span class="sxs-lookup"><span data-stu-id="a51c2-103">The FileTransport sample demonstrates how to configure [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to use File ports, instead of SQL ports.</span></span> <span data-ttu-id="a51c2-104">FileTransport 範例使用「檔案傳輸通訊協定」 (FTP) 取代 HTTP 來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="a51c2-104">The FileTransport sample uses File Transport Protocol (FTP) to send and receive messages, instead of HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a51c2-105">本文件假設您安裝 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 只做為內部測試或示範之用。</span><span class="sxs-lookup"><span data-stu-id="a51c2-105">This document assumes that you are installing [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] for internal testing or demonstration purposes only.</span></span> <span data-ttu-id="a51c2-106">它並未規定任何最基本的安全性帳戶或設定。</span><span class="sxs-lookup"><span data-stu-id="a51c2-106">It does not prescribe any minimum-security account or set up.</span></span> <span data-ttu-id="a51c2-107">在本主題的所有程序中，您必須使用具有本機系統管理員權限的帳戶。</span><span class="sxs-lookup"><span data-stu-id="a51c2-107">You must use an account that has local administrative permissions throughout the procedures in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a51c2-108">本範例不支援訊息附件。</span><span class="sxs-lookup"><span data-stu-id="a51c2-108">This sample does not support message attachments.</span></span>  
  
## <a name="filetransport-binding-files"></a><span data-ttu-id="a51c2-109">FileTransport 繫結檔案</span><span class="sxs-lookup"><span data-stu-id="a51c2-109">FileTransport Binding Files</span></span>  
 <span data-ttu-id="a51c2-110">FileTransport 範例包含兩個繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="a51c2-110">The FileTransport sample includes two binding files.</span></span> <span data-ttu-id="a51c2-111">您可使用這兩個繫結檔案的其中一個設定「檔案」連接埠來使用 BTARN 協調流程。</span><span class="sxs-lookup"><span data-stu-id="a51c2-111">You can use each of these binding files to set up File ports for use with a BTARN orchestration.</span></span> <span data-ttu-id="a51c2-112">這些繫結檔案位於*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet \SDK\FileTransport。</span><span class="sxs-lookup"><span data-stu-id="a51c2-112">These binding files are located in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet \SDK\FileTransport.</span></span> <span data-ttu-id="a51c2-113">請在 [記事本] 等編輯器中開啟每個繫結檔案，以查看協調流程、傳送埠、接收埠和接收位置的設定，如下所列。</span><span class="sxs-lookup"><span data-stu-id="a51c2-113">Open each binding file in an editor like Notepad to see the settings for the orchestration, send port, receive port, and receive location, as listed below.</span></span>  
  
-   <span data-ttu-id="a51c2-114">PrivateInitiatorusingFileDrops.xml</span><span class="sxs-lookup"><span data-stu-id="a51c2-114">PrivateInitiatorusingFileDrops.xml</span></span>  
  
    -   <span data-ttu-id="a51c2-115">協調流程：Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess</span><span class="sxs-lookup"><span data-stu-id="a51c2-115">Orchestration: Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess</span></span>  
  
    -   <span data-ttu-id="a51c2-116">傳送埠：PrivateInitiator_To_File</span><span class="sxs-lookup"><span data-stu-id="a51c2-116">Send port: PrivateInitiator_To_File</span></span>  
  
    -   <span data-ttu-id="a51c2-117">接收埠：File_To_PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="a51c2-117">Receive port: File_To_PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="a51c2-118">接收位置：File_To_PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="a51c2-118">Receive location: File_To_PrivateInitiator</span></span>  
  
-   <span data-ttu-id="a51c2-119">PrivateResponderusingFileDrops.xml</span><span class="sxs-lookup"><span data-stu-id="a51c2-119">PrivateResponderusingFileDrops.xml</span></span>  
  
    -   <span data-ttu-id="a51c2-120">協調流程：Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess</span><span class="sxs-lookup"><span data-stu-id="a51c2-120">Orchestration: Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess</span></span>  
  
    -   <span data-ttu-id="a51c2-121">傳送埠：PrivateResponder_To_File</span><span class="sxs-lookup"><span data-stu-id="a51c2-121">Send port: PrivateResponder_To_File</span></span>  
  
    -   <span data-ttu-id="a51c2-122">接收埠：File_To_PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="a51c2-122">Receive port: File_To_PrivateResponder</span></span>  
  
    -   <span data-ttu-id="a51c2-123">接收位置：File_To_PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="a51c2-123">Receive location: File_To_PrivateResponder</span></span>  
  
 <span data-ttu-id="a51c2-124">下述程序描述如何使用 BTSTask 命令從繫結檔案匯入繫結。</span><span class="sxs-lookup"><span data-stu-id="a51c2-124">The following procedure describes how to import the bindings from the binding files using the BTSTask command.</span></span> <span data-ttu-id="a51c2-125">如需詳細資訊，請參閱 BizTalk Server 說明中的"< ImportBindings 命令 > 主題。</span><span class="sxs-lookup"><span data-stu-id="a51c2-125">For more information, see the "ImportBindings Command" topic in BizTalk Server Help.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a51c2-126">程序</span><span class="sxs-lookup"><span data-stu-id="a51c2-126">Procedure</span></span>  
  
#### <a name="to-set-up-btarn-by-using-file-drop-folders"></a><span data-ttu-id="a51c2-127">使用檔案放置資料夾設定 BTARN</span><span class="sxs-lookup"><span data-stu-id="a51c2-127">To set up BTARN by using file drop folders</span></span>  
  
1.  <span data-ttu-id="a51c2-128">開啟 [BizTalk 總管]。</span><span class="sxs-lookup"><span data-stu-id="a51c2-128">Open BizTalk Explorer.</span></span>  
  
2.  <span data-ttu-id="a51c2-129">停止 PrivateInitiator_To_LOB 和 PrivateResponder_To_LOB 這兩個 LOB SQL 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a51c2-129">Stop the two LOB SQL send ports, PrivateInitiator_To_LOB and PrivateResponder_To_LOB.</span></span>  
  
3.  <span data-ttu-id="a51c2-130">停用 LOB_To_PrivateInitiator 和 LOB_To_PrivateResponder 這兩個 LOB SQL 接收埠。</span><span class="sxs-lookup"><span data-stu-id="a51c2-130">Disable the two Lob SQL Receive ports, LOB_To_PrivateInitiator and LOB_To_PrivateResponder.</span></span>  
  
4.  <span data-ttu-id="a51c2-131">取消登錄 Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess。</span><span class="sxs-lookup"><span data-stu-id="a51c2-131">Unenlist Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess.</span></span>  
  
5.  <span data-ttu-id="a51c2-132">取消登錄 Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess。</span><span class="sxs-lookup"><span data-stu-id="a51c2-132">Unenlist Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess.</span></span>  
  
6.  <span data-ttu-id="a51c2-133">建立 \FileDrops 資料夾，C:\Program Files\Microsoft BizTalk 的 BTARN 資料夾下\<版本\>Accelerator for RosettaNet，然後再建立 \FileDrops 底下的下列資料夾結構：</span><span class="sxs-lookup"><span data-stu-id="a51c2-133">Create a \FileDrops folder under the BTARN folder of C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet , and then create the following folder structure under \FileDrops:</span></span>  
  
    -   <span data-ttu-id="a51c2-134">\PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="a51c2-134">\PrivateInitiator</span></span>  
  
         <span data-ttu-id="a51c2-135">\FromLOB</span><span class="sxs-lookup"><span data-stu-id="a51c2-135">\FromLOB</span></span>  
  
         <span data-ttu-id="a51c2-136">\ToLOB</span><span class="sxs-lookup"><span data-stu-id="a51c2-136">\ToLOB</span></span>  
  
    -   <span data-ttu-id="a51c2-137">\PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="a51c2-137">\PrivateResponder</span></span>  
  
         <span data-ttu-id="a51c2-138">\FromLOB</span><span class="sxs-lookup"><span data-stu-id="a51c2-138">\FromLOB</span></span>  
  
         <span data-ttu-id="a51c2-139">\ToLOB</span><span class="sxs-lookup"><span data-stu-id="a51c2-139">\ToLOB</span></span>  
  
7.  <span data-ttu-id="a51c2-140">執行下列命令 (假設 BTARN 安裝在 C: 磁碟機)：</span><span class="sxs-lookup"><span data-stu-id="a51c2-140">Run the following command (assuming that BTARN is installed on the C: drive):</span></span>  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateInitiatorusingFileDrops.xml  
    ```  
  
8.  <span data-ttu-id="a51c2-141">執行下列命令 (假設 BTARN 安裝在 C: 磁碟機)：</span><span class="sxs-lookup"><span data-stu-id="a51c2-141">Run the following command (assuming that BTARN is installed on the C: drive):</span></span>  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateResponderusingFileDrops.xml  
    ```  
  
9. <span data-ttu-id="a51c2-142">啟動傳送埠：PrivateInitiator_To_File 和 PrivateResponder_To_File。</span><span class="sxs-lookup"><span data-stu-id="a51c2-142">Start the send ports: PrivateInitiator_To_File and PrivateResponder_To_File.</span></span>  
  
10. <span data-ttu-id="a51c2-143">啟用接收埠：LOB_To_PrivateInitiator 和 LOB_To_PrivateResponder。</span><span class="sxs-lookup"><span data-stu-id="a51c2-143">Enable the receive ports: LOB_To_PrivateInitiator and LOB_To_PrivateResponder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a51c2-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="a51c2-144">See Also</span></span>  
 [<span data-ttu-id="a51c2-145">傳訊範例</span><span class="sxs-lookup"><span data-stu-id="a51c2-145">Messaging Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)
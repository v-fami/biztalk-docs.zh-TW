---
title: 步驟 11： 測試 AS2 方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 184ed8ee-6778-4bb9-b265-a94a1fed03cb
caps.latest.revision: 34
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31fbb336d4fb6ba7184a7745520603923c67ce4f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996239"
---
# <a name="step-11-test-the-as2-solution"></a><span data-ttu-id="35ebb-102">步驟 11： 測試 AS2 方案</span><span class="sxs-lookup"><span data-stu-id="35ebb-102">Step 11: Test the AS2 Solution</span></span>
<span data-ttu-id="35ebb-103">![步驟 11 之 11](../core/media/tut-step11-of-11.gif "Tut_Step11_of_11")</span><span class="sxs-lookup"><span data-stu-id="35ebb-103">![Step 11 of 11](../core/media/tut-step11-of-11.gif "Tut_Step11_of_11")</span></span>  
  
 <span data-ttu-id="35ebb-104">在這個步驟中，您將驗證本教學課程的結果。</span><span class="sxs-lookup"><span data-stu-id="35ebb-104">In this step you verify the results of this tutorial.</span></span>  
  
 <span data-ttu-id="35ebb-105">您必須建置用來將 EDI 訊息傳送到 Receive_AS2 接收位置的 Sender.exe 檔案 (透過 Contoso 虛擬目錄)。</span><span class="sxs-lookup"><span data-stu-id="35ebb-105">You need to build the Sender.exe file that you use to send an EDI message to the Receive_AS2 receive location (through the Contoso virtual directory).</span></span> <span data-ttu-id="35ebb-106">Sender.exe 會傳回非同步的 MDN 訊息。</span><span class="sxs-lookup"><span data-stu-id="35ebb-106">Sender.exe returns an asynchronous MDN message.</span></span> <span data-ttu-id="35ebb-107">訊息檔案為 X12_00401_864.edi，位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="35ebb-107">The message file is X12_00401_864.edi located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial folder.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="35ebb-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="35ebb-108">Prerequisites</span></span>  
 <span data-ttu-id="35ebb-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="35ebb-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-test-the-solution-with-an-asynchronous-edi-message"></a><span data-ttu-id="35ebb-110">若要使用非同步 EDI 訊息測試方案</span><span class="sxs-lookup"><span data-stu-id="35ebb-110">To test the solution with an asynchronous EDI message</span></span>  
  
1. <span data-ttu-id="35ebb-111">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender 資料夾中的 Sender.csproj 專案。</span><span class="sxs-lookup"><span data-stu-id="35ebb-111">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the Sender.csproj project in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender folder.</span></span> <span data-ttu-id="35ebb-112">Sender 專案中，以滑鼠右鍵按一下，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="35ebb-112">Right-click the Sender project, and then click **Properties**.</span></span> <span data-ttu-id="35ebb-113">按一下 **簽署**左邊的主控台中。</span><span class="sxs-lookup"><span data-stu-id="35ebb-113">Click **Signing** in the left-hand console.</span></span> <span data-ttu-id="35ebb-114">請確認**簽署組件**已選取此項目，並設定為強式名稱金鑰檔**Sender.snk**。</span><span class="sxs-lookup"><span data-stu-id="35ebb-114">Ensure that **Sign the assembly** is selected, and set the strong name key file to **Sender.snk**.</span></span> <span data-ttu-id="35ebb-115">請確定**僅延遲簽署**已清除。</span><span class="sxs-lookup"><span data-stu-id="35ebb-115">Make sure that **Delay sign only** is cleared.</span></span>  
  
2. <span data-ttu-id="35ebb-116">建置專案。</span><span class="sxs-lookup"><span data-stu-id="35ebb-116">Build the project.</span></span>  
  
3. <span data-ttu-id="35ebb-117">開啟命令提示字元，並瀏覽至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug。</span><span class="sxs-lookup"><span data-stu-id="35ebb-117">Open a command prompt and navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Sender\bin\debug.</span></span> <span data-ttu-id="35ebb-118">Enter `Sender.exe`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="35ebb-118">Enter `Sender.exe`, and then press **Enter**.</span></span> <span data-ttu-id="35ebb-119">確認您看到一則訊息，指出 AS2 訊息已傳送成功，然後再關閉命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="35ebb-119">Verify that you see a message indicating that an AS2 message was successfully sent, and then close the command prompt.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="35ebb-120">執行 Sender.exe 建置 AS2 訊息，其中包含下列 EDI 測試交換： [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\X12_00401_864.edi。</span><span class="sxs-lookup"><span data-stu-id="35ebb-120">Running Sender.exe builds an AS2 message containing the following EDI test interchange: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\X12_00401_864.edi.</span></span> <span data-ttu-id="35ebb-121">建置 AS2 訊息之後，它會將訊息張貼到 Contoso 虛擬目錄，再由此虛擬目錄使用 BTSHttpReceive.dll 將訊息傳送到接收位置。</span><span class="sxs-lookup"><span data-stu-id="35ebb-121">After building the AS2 message, it posts it to the Contoso virtual directory, which uses BTSHttpReceive.dll to route the message to the receive location.</span></span>  
  
4. <span data-ttu-id="35ebb-122">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="35ebb-122">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_MDNToFabrikam folder.</span></span> <span data-ttu-id="35ebb-123">確認沒有\<GUID\>.msg 檔案的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="35ebb-123">Verify that there is a \<GUID\>.msg file in the folder.</span></span> <span data-ttu-id="35ebb-124">使用「記事本」開啟檔案，並確認該訊息是 MDN，而且其中的 AS2-From 已設定為 Contoso， AS2-To 則設定為 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="35ebb-124">Open the file in Notepad, and verify that the message is an MDN with AS2-From set to Contoso and AS2-To set to Fabrikam.</span></span>  
  
5. <span data-ttu-id="35ebb-125">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso 資料夾。</span><span class="sxs-lookup"><span data-stu-id="35ebb-125">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso folder.</span></span> <span data-ttu-id="35ebb-126">確認沒有\<GUID\>資料夾中的.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="35ebb-126">Verify that there is a \<GUID\>.xml file in the folder.</span></span> <span data-ttu-id="35ebb-127">按兩下檔案，並確認訊息的 ST01 欄位設定為 864。</span><span class="sxs-lookup"><span data-stu-id="35ebb-127">Double-click the file, and verify that the ST01 field of the message is set to 864.</span></span>  
  
6. <span data-ttu-id="35ebb-128">瀏覽至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam 資料夾。</span><span class="sxs-lookup"><span data-stu-id="35ebb-128">Navigate to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam folder.</span></span> <span data-ttu-id="35ebb-129">確認沒有\<GUID\>.msg 檔案的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="35ebb-129">Verify that there is a \<GUID\>.msg file in the folder.</span></span> <span data-ttu-id="35ebb-130">使用「記事本」開啟檔案，並確認訊息是 997 訊息 (ST1 為 997)，而且 EDI 內容上方有 AS2 標頭。</span><span class="sxs-lookup"><span data-stu-id="35ebb-130">Open the file in Notepad, and verify that the message is a 997 message (with an ST1 of 997) with AS2 headers over an EDI payload.</span></span> <span data-ttu-id="35ebb-131">確認 AS2-From 是 Contoso，而 AS2-To 則是 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="35ebb-131">Verify that AS2-From is Contoso and AS2-To is Fabrikam.</span></span> <span data-ttu-id="35ebb-132">確認 ISA6 (傳送者識別項) 設定為 1234567 (Contoso)，而 ISA8 (接收者識別項) 則設定為 7654321 (Fabrikam)。</span><span class="sxs-lookup"><span data-stu-id="35ebb-132">Verify that ISA6 (Sender identifier) is set to 1234567 (Contoso) and ISA8 (Receiver identifier) is set to 7654321 (Fabrikam).</span></span>  
  
7. <span data-ttu-id="35ebb-133">若要查看 AS2 和 EDI 狀態報告，請前往**群組中樞**頁面在 BizTalk Server 管理主控台中，捲動到底部的頁面上，按一下其中一個狀態報告連結。</span><span class="sxs-lookup"><span data-stu-id="35ebb-133">To see the AS2 and EDI status reports, go to the **Group Hub** page in the BizTalk Server Administration Console, scroll to the bottom of the page, and click one of the status report links.</span></span> <span data-ttu-id="35ebb-134">如需詳細資訊，請參閱 < [EDI 和 AS2 狀態報告](../core/edi-and-as2-status-reporting.md)。</span><span class="sxs-lookup"><span data-stu-id="35ebb-134">For more information, see [EDI and AS2 Status Reporting](../core/edi-and-as2-status-reporting.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="35ebb-135">後續步驟</span><span class="sxs-lookup"><span data-stu-id="35ebb-135">Next Steps</span></span>  
 <span data-ttu-id="35ebb-136">您已經完成 AS2 教學課程。</span><span class="sxs-lookup"><span data-stu-id="35ebb-136">You have completed the AS2 Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ebb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35ebb-137">See Also</span></span>  
 <span data-ttu-id="35ebb-138">[教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="35ebb-138">[Tutorial 3: AS2 Tutorial](../core/tutorial-3-as2-tutorial.md) </span></span>  
 [<span data-ttu-id="35ebb-139">步驟 1：準備 AS2 教學課程</span><span class="sxs-lookup"><span data-stu-id="35ebb-139">Step 1: Prepare for the AS2 Tutorial</span></span>](../core/step-1-prepare-for-the-as2-tutorial.md)
---
title: 步驟 1： 準備 EDI 介面開發人員教學課程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9be1bddf-d673-4054-87f5-0205b8b5cc0d
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b222e425f44e58d79ab65d848a7aff395b1284b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279230"
---
# <a name="step-1-prepare-for-the-edi-interface-developer-tutorial"></a><span data-ttu-id="0d657-102">步驟 1： 準備 EDI 介面開發人員教學課程</span><span class="sxs-lookup"><span data-stu-id="0d657-102">Step 1: Prepare for the EDI Interface Developer Tutorial</span></span>
<span data-ttu-id="0d657-103">![步驟 1 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")</span><span class="sxs-lookup"><span data-stu-id="0d657-103">![Step 1 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")</span></span>  
  
 <span data-ttu-id="0d657-104">EDI 介面開發人員教學課程是在單一電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="0d657-104">The EDI Interface Development tutorial is run on a single computer.</span></span> <span data-ttu-id="0d657-105">若要準備進行教學課程，您必須安裝及設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中所述[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)。</span><span class="sxs-lookup"><span data-stu-id="0d657-105">To prepare for the tutorial, you must install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as described in [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).</span></span> <span data-ttu-id="0d657-106">您也必須新增 BizTalk EDI 應用程式的參考。</span><span class="sxs-lookup"><span data-stu-id="0d657-106">You must also add reference to the BizTalk EDI Application</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d657-107">此教學課程中，它必須執行使用 IIS 7.5 或 IIS 8 的平台上。</span><span class="sxs-lookup"><span data-stu-id="0d657-107">For this tutorial to work, it must be run on a platform using IIS 7.5 or IIS 8.</span></span>  
  
 <span data-ttu-id="0d657-108">EDI 介面開發人員教學課程所需檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0d657-108">The files required for the EDI Interface Developer tutorial are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial folder.</span></span> <span data-ttu-id="0d657-109">教學課程所需的資料夾和檔案如下：</span><span class="sxs-lookup"><span data-stu-id="0d657-109">The folders and files required for the tutorial are as follows:</span></span>  
  
|<span data-ttu-id="0d657-110">資料夾\檔案</span><span class="sxs-lookup"><span data-stu-id="0d657-110">Folder\File</span></span>|<span data-ttu-id="0d657-111">目的</span><span class="sxs-lookup"><span data-stu-id="0d657-111">Purpose</span></span>|  
|------------------|-------------|  
|<span data-ttu-id="0d657-112">\SDK\EDI Interface Developer Tutorial\EDI Inbound Processing.sln</span><span class="sxs-lookup"><span data-stu-id="0d657-112">\SDK\EDI Interface Developer Tutorial\EDI Inbound Processing.sln</span></span>|<span data-ttu-id="0d657-113">您在 Visual Studio 用來建立此傳訊實例的解決方案檔案</span><span class="sxs-lookup"><span data-stu-id="0d657-113">The solution file that you use in Visual Studio to create this messaging scenario</span></span>|  
|<span data-ttu-id="0d657-114">\SDK\EDI Interface Developer Tutorial\keyfile.snk</span><span class="sxs-lookup"><span data-stu-id="0d657-114">\SDK\EDI Interface Developer Tutorial\keyfile.snk</span></span>|<span data-ttu-id="0d657-115">解決方案檔案指定的組件金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="0d657-115">The assembly key file specified for the solution file</span></span>|  
|<span data-ttu-id="0d657-116">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\SamplePO.txt</span><span class="sxs-lookup"><span data-stu-id="0d657-116">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\SamplePO.txt</span></span>|<span data-ttu-id="0d657-117">您用來測試解決方案的範例訊息檔案 (4010 850 版)</span><span class="sxs-lookup"><span data-stu-id="0d657-117">The sample message file (version 4010 850) that you use to test the solution</span></span>|  
|<span data-ttu-id="0d657-118">\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\Inbound4010850_to_OrderFile.btm</span><span class="sxs-lookup"><span data-stu-id="0d657-118">\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\Inbound4010850_to_OrderFile.btm</span></span>|<span data-ttu-id="0d657-119">將 850 訊息資料轉換為「訂單系統」所需格式的 BizTalk 對應。</span><span class="sxs-lookup"><span data-stu-id="0d657-119">The BizTalk map that converts the 850 message data into the format required by the Order System.</span></span>|  
|<span data-ttu-id="0d657-120">\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\SendOrderFilePipeline.btp</span><span class="sxs-lookup"><span data-stu-id="0d657-120">\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\SendOrderFilePipeline.btp</span></span>|<span data-ttu-id="0d657-121">處理測試訊息的傳送管線，可將訊息傳送至訂單系統。</span><span class="sxs-lookup"><span data-stu-id="0d657-121">The send pipeline that processes the test message for sending the message to the order system.</span></span>|  
|<span data-ttu-id="0d657-122">\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\X12_00401_850.xsd</span><span class="sxs-lookup"><span data-stu-id="0d657-122">\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\X12_00401_850.xsd</span></span>|<span data-ttu-id="0d657-123">測試訊息的 850 結構描述。</span><span class="sxs-lookup"><span data-stu-id="0d657-123">The 850 schema for the test message.</span></span>|  
<span data-ttu-id="0d657-124">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\fromTHEM</span><span class="sxs-lookup"><span data-stu-id="0d657-124">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\fromTHEM</span></span>|<span data-ttu-id="0d657-125">存放從 Fabrikam 接收而來之輸入 850 訊息的資料夾</span><span class="sxs-lookup"><span data-stu-id="0d657-125">Folder where the inbound 850 message is received from Fabrikam</span></span>|  
|<span data-ttu-id="0d657-126">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toOrderSystem</span><span class="sxs-lookup"><span data-stu-id="0d657-126">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toOrderSystem</span></span>|<span data-ttu-id="0d657-127">輸出 850 訊息的傳送目標資料夾，代表您的「訂單系統」後端應用程式</span><span class="sxs-lookup"><span data-stu-id="0d657-127">Folder where the outbound 850 message is sent to, representing your Order System back-end application</span></span>|  
|<span data-ttu-id="0d657-128">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toTHEM_997</span><span class="sxs-lookup"><span data-stu-id="0d657-128">\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toTHEM_997</span></span>|<span data-ttu-id="0d657-129">997 通知的傳送目標資料夾，代表 Fabrikam</span><span class="sxs-lookup"><span data-stu-id="0d657-129">Folder where the 997 acknowledgment is sent to, representing Fabrikam</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="0d657-130">必要條件</span><span class="sxs-lookup"><span data-stu-id="0d657-130">Prerequisites</span></span>  
 <span data-ttu-id="0d657-131">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="0d657-131">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-add-reference-to-the-biztalk-edi-application"></a><span data-ttu-id="0d657-132">若要加入 BizTalk EDI 應用程式的參考</span><span class="sxs-lookup"><span data-stu-id="0d657-132">To add reference to the BizTalk EDI Application</span></span>  
  
1.  <span data-ttu-id="0d657-133">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台**應用程式**] 節點，以滑鼠右鍵按一下您想要使用 edi，例如 [BizTalk Application 1 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d657-133">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **Applications** node, right-click the application that you want to use for EDI, such as BizTalk Application 1.</span></span> <span data-ttu-id="0d657-134">指向**新增**，然後按一下 參考。</span><span class="sxs-lookup"><span data-stu-id="0d657-134">Point to **Add**, and then click References.</span></span>  
  
2.  <span data-ttu-id="0d657-135">在**新增應用程式參考**對話方塊中，選取**BizTalk EDI 應用程式**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0d657-135">In the **Add Application Reference** dialog box, select **BizTalk EDI Application**, and then click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0d657-136">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0d657-136">Next Steps</span></span>  
 <span data-ttu-id="0d657-137">您建置和部署 Inbound_EDI 組件中所述[步驟 2： 更新和部署教學課程方案](../core/step-2-update-and-deploy-the-tutorial-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="0d657-137">You build and deploy the Inbound_EDI assembly, as described in [Step 2: Update and Deploy the Tutorial Solution](../core/step-2-update-and-deploy-the-tutorial-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d657-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d657-138">See Also</span></span>  
 [<span data-ttu-id="0d657-139">教學課程 2: EDI 介面開發人員教學課程</span><span class="sxs-lookup"><span data-stu-id="0d657-139">Tutorial 2: EDI Interface Developer Tutorial</span></span>](../core/tutorial-2-edi-interface-developer-tutorial.md)
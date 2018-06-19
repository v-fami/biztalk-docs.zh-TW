---
title: 建立管線專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b584e3ab-e824-4977-b4ed-4fc197a6cf7a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eead267abbb990933e6fd3150d099d07b007526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209710"
---
# <a name="creating-a-pipeline-project"></a><span data-ttu-id="a71d9-102">建立管線專案</span><span class="sxs-lookup"><span data-stu-id="a71d9-102">Creating a Pipeline Project</span></span>
<span data-ttu-id="a71d9-103">若要建立管線專案：</span><span class="sxs-lookup"><span data-stu-id="a71d9-103">To create a pipeline project:</span></span>  
  
1.  <span data-ttu-id="a71d9-104">在 Visual Studio 中建立新的 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="a71d9-104">In Visual Studio, create a new BizTalk project.</span></span>  
  
2.  <span data-ttu-id="a71d9-105">將接收管線項目] 和 [傳送管線項目加入專案。</span><span class="sxs-lookup"><span data-stu-id="a71d9-105">Add a receive pipeline item and a send pipeline item to the project.</span></span>  
  
3.  <span data-ttu-id="a71d9-106">開啟 ReceivePipeline.btp 檔。</span><span class="sxs-lookup"><span data-stu-id="a71d9-106">Open the ReceivePipeline.btp file.</span></span>  
  
4.  <span data-ttu-id="a71d9-107">在管線設計師中，開啟 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="a71d9-107">In Pipeline Designer, open the Toolbox.</span></span>  
  
5.  <span data-ttu-id="a71d9-108">以滑鼠右鍵按一下**工具箱**介面，然後再選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="a71d9-108">Right-click the **Toolbox** surface, and then select **Choose Items**.</span></span>  
  
6.  <span data-ttu-id="a71d9-109">在 選擇工具箱項目 視窗中，按一下**管線元件**索引標籤，然後選取 下列管線元件：</span><span class="sxs-lookup"><span data-stu-id="a71d9-109">In the Choose Toolbox Items window, click the **Pipeline Components** tab, and then select the following pipeline components:</span></span>  
  
    -   <span data-ttu-id="a71d9-110">SwiftMXDisassembler</span><span class="sxs-lookup"><span data-stu-id="a71d9-110">SwiftMXDisassembler</span></span>  
  
    -   <span data-ttu-id="a71d9-111">SwiftMXAssembler</span><span class="sxs-lookup"><span data-stu-id="a71d9-111">SwiftMXAssembler</span></span>  
  
    -   <span data-ttu-id="a71d9-112">Swift MXRR 編碼器元件</span><span class="sxs-lookup"><span data-stu-id="a71d9-112">Swift MXRR Encoder Component</span></span>  
  
    -   <span data-ttu-id="a71d9-113">Swift MXRR 解碼器元件</span><span class="sxs-lookup"><span data-stu-id="a71d9-113">Swift MXRR Decoder Component</span></span>  
  
    -   <span data-ttu-id="a71d9-114">Swift MXRR 相互關聯合作對象解析程式元件</span><span class="sxs-lookup"><span data-stu-id="a71d9-114">Swift MXRR Correlation Party Resolver Component</span></span>  
  
7.  <span data-ttu-id="a71d9-115">拖曳**SwiftMXDisassembler**元件到接收管線中的解譯器預留位置。</span><span class="sxs-lookup"><span data-stu-id="a71d9-115">Drag the **SwiftMXDisassembler** component into the Disassembler placeholder in the Receive Pipeline.</span></span>  
  
8.  <span data-ttu-id="a71d9-116">在 SwiftMXDisassembler 元件內容中，設定**BRE 驗證**屬性為 TRUE 或 FALSE 取決於您要傳入訊息上啟用商務規則驗證。</span><span class="sxs-lookup"><span data-stu-id="a71d9-116">In the SwiftMXDisassembler component properties, set the **BRE Validation** property to TRUE or FALSE depending on whether you want to enable Business Rules Validation on the incoming messages.</span></span> <span data-ttu-id="a71d9-117">設定**TransportHeaderRequired**屬性為 TRUE 或 FALSE 取決於您提供傳輸訊息標頭中的。</span><span class="sxs-lookup"><span data-stu-id="a71d9-117">Set the **TransportHeaderRequired** property to TRUE or FALSE depending on whether you want to provide transport header in messages.</span></span>  
  
9. <span data-ttu-id="a71d9-118">Swift MXRR 解碼器和 Swift MXRR 相互關聯合作對象解析程式元件拖曳解碼器和合作對象解析程式內預留位置的接收管線。</span><span class="sxs-lookup"><span data-stu-id="a71d9-118">Drag the Swift MXRR Decoder and Swift MXRR Correlation Party Resolver component into the Decoder and the Party Resolver placeholder inside the Receive Pipeline.</span></span>  
  
10. <span data-ttu-id="a71d9-119">選取**MXRR 相互關聯合作對象解析程式**管線中。</span><span class="sxs-lookup"><span data-stu-id="a71d9-119">Select the **MXRR Correlation Party Resolver** in the pipeline.</span></span> <span data-ttu-id="a71d9-120">在 [管線元件屬性] 視窗中，設定**Enable Logging for 對帳的 BAM**屬性為 TRUE 或 FALSE，根據您要啟用重新調整 SWIFT 的回應。</span><span class="sxs-lookup"><span data-stu-id="a71d9-120">In the Pipeline Component Properties window, set the **Enable BAM Logging for Reconciliation** property to TRUE or FALSE, depending on whether you want to enable reconciliation for the SWIFT responses.</span></span>  
  
11. <span data-ttu-id="a71d9-121">開啟**SendPipeline.btp**檔案，在管線設計師中，開啟**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="a71d9-121">Open the **SendPipeline.btp** file, In the Pipeline Designer, open the **Toolbox**.</span></span>  
  
12. <span data-ttu-id="a71d9-122">在 [工具箱] 拖曳**SwiftMXAssembler**成組譯工具內預留位置的傳送管線元件。</span><span class="sxs-lookup"><span data-stu-id="a71d9-122">In Toolbox, drag the **SwiftMXAssembler** component into the Assembler placeholder inside the Send Pipeline.</span></span>  
  
13. <span data-ttu-id="a71d9-123">拖曳**Swift MXRR 編碼器**到編碼器預留位置的傳送管線元件。</span><span class="sxs-lookup"><span data-stu-id="a71d9-123">Drag the **Swift MXRR Encoder** component into the Encoder placeholders of the Send Pipeline.</span></span>  
  
14. <span data-ttu-id="a71d9-124">選取**MXRR 編碼器合作對象解析程式**在管線中，然後在 [管線元件屬性] 視窗中，設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="a71d9-124">Select the **MXRR Encoder Party Resolver** in the pipeline, and then in the Pipeline Component Properties window, set the following properties.</span></span>  
  
15. <span data-ttu-id="a71d9-125">啟用**BAM 記錄對帳**為 TRUE 或 FALSE 取決於您要啟用重新調整 SWIFT 的回應。</span><span class="sxs-lookup"><span data-stu-id="a71d9-125">Enable **BAM Logging for Reconciliation** to TRUE or FALSE depending on whether you want to enable reconciliation for the SWIFT responses.</span></span>  
  
16. <span data-ttu-id="a71d9-126">設定**LAU 需要**為 TRUE 或 FALSE，視您是否需要啟用 SWIFT 聯盟存取 (SAA) 在訊息的簽章。</span><span class="sxs-lookup"><span data-stu-id="a71d9-126">Set the **LAU Required** to TRUE or FALSE depending on whether you have to enable the signing of the message at the SWIFT Alliance Access (SAA).</span></span>  
  
17. <span data-ttu-id="a71d9-127">如果已 LAU 必要屬性已設定為 TRUE，然後提供 LAU 索引鍵的第一個部分和 LAU 金鑰第二個部分 （值有相同的設定 SAA 時所提供）。</span><span class="sxs-lookup"><span data-stu-id="a71d9-127">If the LAU Required property has been has been set to TRUE, then provide LAU Key First Part and LAU Key Second Part (the values have to be the same ones that were provided while configuring the SAA.)</span></span>  
  
18. <span data-ttu-id="a71d9-128">建置然後再部署專案。</span><span class="sxs-lookup"><span data-stu-id="a71d9-128">Build and then deploy the project.</span></span>
---
title: "執行命名空間元件測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13768608-ade6-44c0-897f-d417c3408302
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae865e91fd6ff796cb870c71840bde8a95831e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-namespace-component-tests"></a><span data-ttu-id="dd87b-102">執行測試命名空間元件</span><span class="sxs-lookup"><span data-stu-id="dd87b-102">Running the Namespace Component Tests</span></span>
<span data-ttu-id="dd87b-103">下列程序顯示如何執行所有的四個測試案例，以供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]命名空間元件 」 範例。</span><span class="sxs-lookup"><span data-stu-id="dd87b-103">The following procedure shows how you can run all four of the test scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Namespace Component sample.</span></span>  
  
 <span data-ttu-id="dd87b-104">**若要執行範例測試案例的命名空間元件**</span><span class="sxs-lookup"><span data-stu-id="dd87b-104">**To run the Namespace Component sample test scenarios**</span></span>  
  
1.  <span data-ttu-id="dd87b-105">您第一次執行此範例之前，請確定該接收位置和傳送連接埠 URL 指向來源發佈檔案中的適當子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-105">Before you run this sample for the first time, make sure that the receive location and send port URL point to the appropriate subfolders in the source distribution files.</span></span> <span data-ttu-id="dd87b-106">指定接收位置的子資料夾 \Source\Samples\Namespace\Test\Filedrop\In 和子資料夾 \Source\Samples\Namespace\Test\Filedrop\Out 傳送連接埠的 url。</span><span class="sxs-lookup"><span data-stu-id="dd87b-106">Specify the subfolder \Source\Samples\Namespace\Test\Filedrop\In for the receive location and the subfolder \Source\Samples\Namespace\Test\Filedrop\Out for the send port URL.</span></span>  
  
2.  <span data-ttu-id="dd87b-107">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="dd87b-107">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
3.  <span data-ttu-id="dd87b-108">建立名為 TEST_Add_to_PassThrough.0000.ns.xml （位於您 ESB 的安裝資料夾的 \Source\Samples\Namespace\Test\Data\ 子資料夾），檔案的副本，並重新命名該複本移除"TEST_"前置詞。</span><span class="sxs-lookup"><span data-stu-id="dd87b-108">Make a copy of the file named TEST_Add_to_PassThrough.0000.ns.xml (located in the \Source\Samples\Namespace\Test\Data\ subfolder of your ESB installation folder), and rename the copy by removing the "TEST_" prefix.</span></span>  
  
4.  <span data-ttu-id="dd87b-109">將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-109">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
5.  <span data-ttu-id="dd87b-110">ESB 拾取訊息、 新增命名空間，和將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-110">The ESB picks up the message, adds a namespace to it, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="dd87b-111">開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。</span><span class="sxs-lookup"><span data-stu-id="dd87b-111">Open the input and output files in a text editor to see the effect of this test.</span></span>  
  
6.  <span data-ttu-id="dd87b-112">現在，執行第二個測試。</span><span class="sxs-lookup"><span data-stu-id="dd87b-112">Now run the second test.</span></span> <span data-ttu-id="dd87b-113">建立一份名為 TEST_Add_to_Remove.0000.ns.xml 檔案並將它重新命名藉由移除"TEST_"前置詞。</span><span class="sxs-lookup"><span data-stu-id="dd87b-113">Make a copy of the file named TEST_Add_to_Remove.0000.ns.xml and rename it by removing the "TEST_" prefix.</span></span>  
  
7.  <span data-ttu-id="dd87b-114">將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-114">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
8.  <span data-ttu-id="dd87b-115">ESB 拾取訊息、 命名空間加入、 移除新的命名空間，及將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-115">The ESB picks up the message, adds a namespace to it, removes the new namespace, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="dd87b-116">開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。</span><span class="sxs-lookup"><span data-stu-id="dd87b-116">Open the input and output files in a text editor to see the effect of this test.</span></span>  
  
9. <span data-ttu-id="dd87b-117">現在，執行第三個測試。</span><span class="sxs-lookup"><span data-stu-id="dd87b-117">Now run the third test.</span></span> <span data-ttu-id="dd87b-118">建立一份名為 TEST_PassThrough_to_Remove.0000.ns.xml 檔案並將它重新命名藉由移除"TEST_"前置詞。</span><span class="sxs-lookup"><span data-stu-id="dd87b-118">Make a copy of the file named TEST_PassThrough_to_Remove.0000.ns.xml and rename it by removing the "TEST_" prefix.</span></span>  
  
10. <span data-ttu-id="dd87b-119">將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-119">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
11. <span data-ttu-id="dd87b-120">ESB 拾取訊息、 移除現有的命名空間，並將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-120">The ESB picks up the message, removes the existing namespace, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="dd87b-121">開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。</span><span class="sxs-lookup"><span data-stu-id="dd87b-121">Open the input and output files in a text editor to see the effect of this test.</span></span>  
  
12. <span data-ttu-id="dd87b-122">最後，執行第四個測試。</span><span class="sxs-lookup"><span data-stu-id="dd87b-122">Finally, run the fourth test.</span></span> <span data-ttu-id="dd87b-123">建立一份名為 TEST_AddViaExtraction_to_PassThrough.0000.ns.xml 檔案並將它重新命名藉由移除"TEST_"前置詞。</span><span class="sxs-lookup"><span data-stu-id="dd87b-123">Make a copy of the file named TEST_AddViaExtraction_to_PassThrough.0000.ns.xml and rename it by removing the "TEST_" prefix.</span></span>  
  
13. <span data-ttu-id="dd87b-124">將重新命名的檔案複製到 \Source\Samples\Namespace\Test\Filedrop\In 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-124">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
14. <span data-ttu-id="dd87b-125">ESB 拾取訊息，會擷取在指定的項目**ExtractionNodeXPath**屬性，從指定的命名空間的值，這個項目中建立訊息，並將更新的訊息置放 \Source\Samples\Namespace\Test\Filedrop\Out 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd87b-125">The ESB picks up the message, extracts the element specified in the **ExtractionNodeXPath** property, creates a message from this element with the specified namespace values, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="dd87b-126">開啟 輸入及輸出檔案中 文字編輯器，以查看這項測試的影響。</span><span class="sxs-lookup"><span data-stu-id="dd87b-126">Open the input and output files in a text editor to see the effect of this test.</span></span>
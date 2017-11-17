---
title: "執行的例外狀況處理服務 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d69e720c-89e4-42c2-b4d0-31f0b865ab7f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a224c985591801bc9622000c35587b7137f933
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-exception-handling-service-sample"></a><span data-ttu-id="300a1-102">執行的例外狀況處理服務範例</span><span class="sxs-lookup"><span data-stu-id="300a1-102">Running the Exception Handling Service Sample</span></span>
<span data-ttu-id="300a1-103">「 例外狀況處理服務 」 範例示範如何使用例外狀況處理 Web 服務才能提交到 ESB 例外狀況處理架構從外部應用程式的錯誤。</span><span class="sxs-lookup"><span data-stu-id="300a1-103">The Exception Handling Service sample demonstrates how to consume the Exception Handling Web Service in order to submit a fault into the ESB Exception Handling Framework from an external application.</span></span> <span data-ttu-id="300a1-104">下列程序執行此範例需要[安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="300a1-104">The following procedure for running this sample requires [Installing the Exception Management Samples](../esb-toolkit/installing-the-exception-management-samples.md).</span></span>  
  
 <span data-ttu-id="300a1-105">**若要執行例外狀況處理的服務範例**</span><span class="sxs-lookup"><span data-stu-id="300a1-105">**To run the Exception Handling Service sample**</span></span>  
  
1.  <span data-ttu-id="300a1-106">在 Windows 檔案總管] 中開啟資料夾 \Source\Samples\ExceptionHandlingService，您的安裝位置[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例，然後再開啟 [Visual Studio 方案檔名為 ExceptionHandlingService.sln。</span><span class="sxs-lookup"><span data-stu-id="300a1-106">In Windows Explorer, open the folder \Source\Samples\ExceptionHandlingService, where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples, and then open the Visual Studio solution file named ExceptionHandlingService.sln.</span></span>  
  
2.  <span data-ttu-id="300a1-107">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，按一下 **開始偵錯**工具列上。</span><span class="sxs-lookup"><span data-stu-id="300a1-107">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], click **Start Debugging** on the Toolbar.</span></span>  
  
3.  <span data-ttu-id="300a1-108">在載入的表單中，按一下 [**產生例外狀況**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="300a1-108">On the form that loads, click the **Generate Exception** button.</span></span>  
  
4.  <span data-ttu-id="300a1-109">在 Windows 檔案總管 中開啟資料夾 \Samples\Exception Handling\Test\Filedrop\All_Exceptions，，然後開啟最新的 Exceptions_ {GUID}.xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="300a1-109">In Windows Explorer, open the folder \Samples\Exception Handling\Test\Filedrop\All_Exceptions, and then open the most recent Exceptions_{GUID}.xml file.</span></span>  
  
5.  <span data-ttu-id="300a1-110">檢查產生的例外狀況的內容。</span><span class="sxs-lookup"><span data-stu-id="300a1-110">Examine the contents of the generated exception.</span></span>  
  
 <span data-ttu-id="300a1-111">如需如何 「 例外狀況處理服務 」 範例使用例外狀況管理服務的詳細資訊，請參閱[例外狀況處理服務範例的運作方式](../esb-toolkit/how-the-exception-handling-service-sample-works.md)。</span><span class="sxs-lookup"><span data-stu-id="300a1-111">For more information about how the Exception Handling Service sample uses the Exception Management service, see [How the Exception Handling Service Sample Works](../esb-toolkit/how-the-exception-handling-service-sample-works.md).</span></span>
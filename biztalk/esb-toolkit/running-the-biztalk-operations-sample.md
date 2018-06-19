---
title: 執行 BizTalk 作業範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e91d4e57-ba94-4730-8c5a-4c96902f313f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57480e6020b2ab262d7d9db522b9dd2f79aa49cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294534"
---
# <a name="running-the-biztalk-operations-sample"></a><span data-ttu-id="c9b30-102">執行 BizTalk 作業範例</span><span class="sxs-lookup"><span data-stu-id="c9b30-102">Running the BizTalk Operations Sample</span></span>
<span data-ttu-id="c9b30-103">Microsoft BizTalk 作業範例會使用 Windows Form 測試用戶端應用程式來執行 BizTalk 作業 Web 服務方法並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="c9b30-103">The Microsoft BizTalk Operations sample uses a Windows Forms test client application to execute methods of the BizTalk Operations Web service and display the results.</span></span> <span data-ttu-id="c9b30-104">您可以開啟測試用戶端專案來執行它，並檢查以查看如何使用您自己的服務導向架構 (SOA) 和 ESB 應用程式中的 BizTalk 作業 Web 服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9b30-104">You can open the test client project to run it and to examine the code to see how you can use the BizTalk Operations Web service in your own service-oriented architecture (SOA) and ESB applications.</span></span>  
  
 <span data-ttu-id="c9b30-105">在 Windows 檔案總管 中開啟 \Samples\BizTalkOperations\bin\Debug，名為的資料夾並執行應用程式 Microsoft.Practices.ESB.BizTalkOperations.Test.Client.exe。</span><span class="sxs-lookup"><span data-stu-id="c9b30-105">In Windows Explorer, open the folder named \Samples\BizTalkOperations\bin\Debug, and then execute the application Microsoft.Practices.ESB.BizTalkOperations.Test.Client.exe.</span></span>  
  
 <span data-ttu-id="c9b30-106">圖 1 顯示 BizTalk 作業 Web 服務測試用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9b30-106">Figure 1 shows the test client application for the BizTalk Operations Web service.</span></span> <span data-ttu-id="c9b30-107">您可以執行使用此應用程式的 BizTalk 作業 Web 服務的所有函式。</span><span class="sxs-lookup"><span data-stu-id="c9b30-107">You can execute all the functions of the BizTalk Operations Web service using this application.</span></span> <span data-ttu-id="c9b30-108">應用程式會將結果顯示在樹狀檢視格式，並顯示服務所傳回的訊息。</span><span class="sxs-lookup"><span data-stu-id="c9b30-108">The application displays the results in a tree-view format and shows the message returned by the service.</span></span>  
  
 <span data-ttu-id="c9b30-109">![Web 服務測試](../esb-toolkit/media/ch6-webservicetest.gif "第 6 章第 WebServiceTest")</span><span class="sxs-lookup"><span data-stu-id="c9b30-109">![Web Service Test](../esb-toolkit/media/ch6-webservicetest.gif "Ch6-WebServiceTest")</span></span>  
  
 <span data-ttu-id="c9b30-110">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="c9b30-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="c9b30-111">**BizTalk 作業 Web 服務測試用戶端**</span><span class="sxs-lookup"><span data-stu-id="c9b30-111">**The BizTalk Operations Web Service Test Client**</span></span>  
  
 <span data-ttu-id="c9b30-112">若要執行 BizTalk 作業 Web 服務不需要任何參數的方法，只要按一下適當的按鈕，在應用程式視窗的左半部。</span><span class="sxs-lookup"><span data-stu-id="c9b30-112">To execute a method of the BizTalk Operations Web service that does not require any parameters, simply click the appropriate button in the left side of the application window.</span></span> <span data-ttu-id="c9b30-113">方法需要輸入的參數，在視窗頂端的下拉式清單中選取的方法，針對輸入參數值，您需要此項目，然後再按一下**叫用服務** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c9b30-113">For methods that do require input parameters, select the method in the drop-down list at the top of the window, enter the parameter values you require, and then click the **Invoke Service** button.</span></span>  
  
## <a name="how-the-sample-works"></a><span data-ttu-id="c9b30-114">範例的運作方式</span><span class="sxs-lookup"><span data-stu-id="c9b30-114">How the Sample Works</span></span>  
 <span data-ttu-id="c9b30-115">範例應用程式具現化 ESB BizTalk 作業 Web 服務，並呼叫適當的方法取決於您在應用程式中選取此設定。</span><span class="sxs-lookup"><span data-stu-id="c9b30-115">The sample application instantiates the ESB BizTalk Operations Web service and calls the appropriate method depending on the settings you select in the application.</span></span> <span data-ttu-id="c9b30-116">它會將您在中輸入應用程式控制項做為參數至所選的服務的方法，將值傳遞，並會收集應用程式視窗中顯示此服務方法的輸出。</span><span class="sxs-lookup"><span data-stu-id="c9b30-116">It passes the value(s) you enter in the application controls as parameters to the selected service method, and it collects the output from the service method to display in the application window.</span></span>
---
title: "執行自訂的路線案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fd69e29-e853-4b16-9966-29ab98dd5bea
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8659c5b37cba0520fb4a4c0f4c63c8d6ecff37be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="execute-a-custom-itinerary-scenario"></a><span data-ttu-id="2569a-102">執行自訂的路線案例</span><span class="sxs-lookup"><span data-stu-id="2569a-102">Execute a Custom Itinerary Scenario</span></span>
<span data-ttu-id="2569a-103">您可以使用路線測試用戶端應用程式執行路線的自訂案例。</span><span class="sxs-lookup"><span data-stu-id="2569a-103">You can use the Itinerary Test Client application execute custom itinerary scenarios.</span></span>  
  
### <a name="to-execute-a-custom-itinerary-scenario-using-the-itinerary-test-client-application"></a><span data-ttu-id="2569a-104">若要執行的自訂的路線案例，使用行程測試用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="2569a-104">To execute a custom itinerary scenario using the Itinerary Test Client application</span></span>  
  
1.  <span data-ttu-id="2569a-105">在 Windows 檔案總管 中開啟資料夾 \Source\Samples\Itinerary\Source\ESB。您的安裝位置的 Itinerary.Test\bin\Debug[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]範例和啟動名為 Esb.Itinerary.Test.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2569a-105">In Windows Explorer, open the folder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug where you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] samples and start the application named Esb.Itinerary.Test.exe.</span></span>  
  
2.  <span data-ttu-id="2569a-106">選取的服務型別在**ServiceType**下拉式清單中，指定要求的名稱，然後再選取**IsRequestResponse**核取方塊，如果這是要求/回應作業。</span><span class="sxs-lookup"><span data-stu-id="2569a-106">Select a service type in the **ServiceType** drop-down list, specify a name for the request, and then select the **IsRequestResponse** check box if this is a request/response operation.</span></span> <span data-ttu-id="2569a-107">您可以指定雙向作業，並選擇使用 WCF 路線 Web 服務版本。若要這樣做，請選取 核取方塊後**Web 服務選項**應用程式視窗的頂端區段。</span><span class="sxs-lookup"><span data-stu-id="2569a-107">You can specify a two-way operation and choose to use the WCF version of the Itinerary Web service; to do this, select the check boxes in the **Web Service Options** section at the top of the application window.</span></span>  
  
3.  <span data-ttu-id="2569a-108">若要指定具有所選的服務中使用解析程式**AddResolversfortheService**視窗的區段，選取解析程式輸入從下拉式清單中，然後按一下**AddResolver**。</span><span class="sxs-lookup"><span data-stu-id="2569a-108">To specify the resolvers to use with the selected service in the **AddResolversfortheService** section of the window, select a resolver type from the drop-down list, and then click **AddResolver**.</span></span> <span data-ttu-id="2569a-109">視需要，您可以新增一個以上的解析程式。</span><span class="sxs-lookup"><span data-stu-id="2569a-109">You can add more than one resolver if required.</span></span> <span data-ttu-id="2569a-110">加入所有必要的解析程式之後，按一下**AddService**將叫用的服務新增至路線 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2569a-110">After you add all the required resolvers, click the **AddService** button to add this service invocation to the itinerary.</span></span>  
  
4.  <span data-ttu-id="2569a-111">如果您想要將多個服務引動過程新增至路線，重複步驟 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="2569a-111">If you want to add more service invocations to the itinerary, repeat steps 2 and 3.</span></span> <span data-ttu-id="2569a-112">您也可以使用**RemoveService**和**ClearServices**按鈕，以修改在路線服務的清單。</span><span class="sxs-lookup"><span data-stu-id="2569a-112">You can also use the **RemoveService** and **ClearServices** buttons to modify the list of services in the itinerary.</span></span>  
  
5.  <span data-ttu-id="2569a-113">如果您想要重複目前行程，在其他時候，完成目前的路線磁碟按一下儲存**SaveItinerary**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="2569a-113">If you want to repeat the current itinerary at another time, save the complete current itinerary to disk by clicking the **SaveItinerary** button.</span></span> <span data-ttu-id="2569a-114">您可以重新載入，即可**LoadItinerary**  按鈕。</span><span class="sxs-lookup"><span data-stu-id="2569a-114">You can load it again by clicking the **LoadItinerary** button.</span></span> <span data-ttu-id="2569a-115">這表示您沒有指定的服務和解析程式在路線每次您執行此案例中使用不同的訊息或路線的 Web 服務設定。</span><span class="sxs-lookup"><span data-stu-id="2569a-115">This means that you do not have to specify the services and resolvers in the itinerary every time you execute this scenario with different messages or Itinerary Web service settings.</span></span>  
  
6.  <span data-ttu-id="2569a-116">載入適當的訊息。</span><span class="sxs-lookup"><span data-stu-id="2569a-116">Load a suitable message.</span></span> <span data-ttu-id="2569a-117">若要這樣做，請輸入的路徑和名稱中的訊息**LoadMessage**文字方塊或按一下省略符號按鈕 （...），並選取必要的訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="2569a-117">To do this, either type the path and name of the message in the **LoadMessage** text box or click the ellipsis button (...), and then select the required message file.</span></span>  
  
7.  <span data-ttu-id="2569a-118">按一下**SubmitRequest**送出訊息以進行處理，您所指定的計劃設定的按鈕。</span><span class="sxs-lookup"><span data-stu-id="2569a-118">Click the **SubmitRequest** button to submit the message for processing with the itinerary settings you specified.</span></span> <span data-ttu-id="2569a-119">如果處理程序傳回結果，這會顯示在**結果**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="2569a-119">If the processing returns a result, this will appear in the **Result** text box.</span></span>
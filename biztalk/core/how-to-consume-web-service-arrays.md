---
title: "如何使用 Web 服務陣列 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, Web services
- Web services, arrays
- orchestrations, Web services
- orchestrations, Web ports
ms.assetid: 29ecaaed-aa8a-4cf9-a7c8-4b0d6dd412ac
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e78f12405c9c331a888a268d39e2a1520c84fdc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-consume-web-service-arrays"></a><span data-ttu-id="d4d8b-102">如何使用 Web 服務陣列</span><span class="sxs-lookup"><span data-stu-id="d4d8b-102">How to Consume Web Service Arrays</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d4d8b-103"> 讓您能夠從 [BizTalk 協調流程] 使用 Web 服務中公開的陣列。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-103"> provides the ability to consume arrays that are exposed in Web services from a BizTalk Orchestration.</span></span>  
  
 <span data-ttu-id="d4d8b-104">**若要設定協調流程 使用 Web 服務中公開的陣列：**</span><span class="sxs-lookup"><span data-stu-id="d4d8b-104">**To configure an Orchestration to consume an array exposed in a Web service:**</span></span>  
  
 <span data-ttu-id="d4d8b-105">決定公開陣列之 Web 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-105">Determine the URL for the Web service that exposes arrays.</span></span> <span data-ttu-id="d4d8b-106">通常是 asmx 網頁，其中列出 Web 服務支援的作業。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-106">This is typically an asmx Web page that lists the operations supported by the Web service.</span></span> <span data-ttu-id="d4d8b-107">例如： http://localhost/ArrayWS/ArraySvc.asmx。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-107">For example: http://localhost/ArrayWS/ArraySvc.asmx.</span></span>  
  
1.  <span data-ttu-id="d4d8b-108">在包含協調流程的 Visual Studio 專案中新增此 URL 的 Web 參考：</span><span class="sxs-lookup"><span data-stu-id="d4d8b-108">Add a Web reference to this URL in the Visual Studio project that contains your orchestration:</span></span>  
  
    -   <span data-ttu-id="d4d8b-109">在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**加入服務參考**。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-109">In the Solution Explorer, right-click **References**, and click **Add Service Reference**.</span></span>  
  
    -   <span data-ttu-id="d4d8b-110">在**加入服務參考**對話方塊中，按一下 **進階**。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-110">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
    -   <span data-ttu-id="d4d8b-111">在**服務參考設定**對話方塊中，按一下 **加入 Web 參考**中**相容性**> 一節。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-111">In the **Service Reference Settings** dialog box, click **Add Web Reference** in the **Compatibility** section.</span></span>  
  
    -   <span data-ttu-id="d4d8b-112">在**加入 Web 參考**對話方塊方塊中，輸入 Web 服務的 URL **URL**文字方塊中，然後按一下**移**。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-112">In the **Add Web Reference** dialog box, enter the URL for the Web service into the **URL** text box and then click **Go**.</span></span>  
  
    -   <span data-ttu-id="d4d8b-113">輸入 Web 參考到名稱**Web 參考名稱**文字方塊中，然後按一下**加入參考** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-113">Enter a name for the Web reference into the **Web reference name** text box and click the **Add Reference** button.</span></span>  
  
    -   <span data-ttu-id="d4d8b-114">Web 參考會出現在**Web 參考**在 [方案總管] 中。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-114">The Web reference will appear under **Web References** in the Solution Explorer.</span></span>  
  
        > [!TIP]
        >  <span data-ttu-id="d4d8b-115">將 Web 參考加入至專案中，一旦**加入 Web 參考**命令時，直接使用您以滑鼠右鍵按一下專案名稱或**參考**或**的Web參考**.</span><span class="sxs-lookup"><span data-stu-id="d4d8b-115">Once you have a Web reference added to the project, the **Add Web Reference** command is directly available when you right-click the project name or **References** or **Web References**.</span></span>  
  
2.  <span data-ttu-id="d4d8b-116">新增 Web 連接埠至協調流程：</span><span class="sxs-lookup"><span data-stu-id="d4d8b-116">Add a Web port to your orchestration:</span></span>  
  
    -   <span data-ttu-id="d4d8b-117">拖曳**連接埠**圖形從工具箱拖曳至其中一個連接埠介面，以啟動協調流程設計師**連接埠組態精靈**。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-117">Drag a **Port** shape from the toolbox to one of the port surfaces in the Orchestration Designer to launch the **Port Configuration Wizard**.</span></span> <span data-ttu-id="d4d8b-118">按一下**下一步**按鈕**連接埠組態精靈**顯示**連接埠內容**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-118">Click the **Next** button in the **Port Configuration Wizard** to display the **Port Properties** dialog.</span></span>  
  
    -   <span data-ttu-id="d4d8b-119">輸入值**名稱**文字方塊中，以找出連接埠，然後按一下**下一步** 按鈕以顯示**選取連接埠類型**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-119">Enter a value into the **Name** text box to identify the port, and click the **Next** button to display the **Select a Port Type** dialog.</span></span>  
  
    -   <span data-ttu-id="d4d8b-120">選取的選項**使用現有的連接埠類型**，選取 [Web 連接埠類型，對應至 Web 參考您加入，然後按一下**下一步**] 按鈕以顯示**連接埠繫結**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-120">Select the option to **Use an existing Port Type**, select the Web Port type that corresponds to the Web reference you added, and click the **Next** button to display the **Port Binding** dialog.</span></span>  
  
    -   <span data-ttu-id="d4d8b-121">在**連接埠繫結**對話方塊中選取適當**連接埠繫結**選項，然後按一下**下一步**按鈕，然後按一下**完成**按鈕。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-121">In the **Port Binding** dialog select the appropriate **Port binding** option and click the **Next** button, then click the **Finish** button.</span></span> <span data-ttu-id="d4d8b-122">現在，包含 Web 服務支援之作業的 [協調流程設計師] 中應該會顯示 Web 連接埠。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-122">You should now have a Web port displayed in the Orchestration Designer that includes the operations supported by the Web service.</span></span>  
  
3.  <span data-ttu-id="d4d8b-123">新增**傳送**和**接收**到適當協調流程的圖形：</span><span class="sxs-lookup"><span data-stu-id="d4d8b-123">Add **Send** and **Receive** shapes to your Orchestration as appropriate:</span></span>  
  
    -   <span data-ttu-id="d4d8b-124">拖曳**傳送**圖形的連接線，設定讓協調流程將要求訊息傳送至 Web 連接埠協調流程設計師介面 中從 工具箱。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-124">Drag a **Send** shape from the toolbox to a connecting line in the Orchestration Designer surface to configure the orchestration to send a request message to the Web port.</span></span> <span data-ttu-id="d4d8b-125">如果您連接**傳送**圖形以其中一個 Web 連接埠要求訊息連接器，BizTalk 將自動建立傳送要求訊息至此連接埠時所要使用的適當類型訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-125">If you connect the **Send** shape to one of the Web port request message connectors, BizTalk will automatically create a message of the appropriate type to be used when sending a request message to this port.</span></span>  
  
    -   <span data-ttu-id="d4d8b-126">拖曳**接收**圖形的連接線，設定讓協調流程從 Web 連接埠接收回應訊息的協調流程設計師介面 中從 工具箱。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-126">Drag a **Receive** shape from the toolbox to a connecting line in the Orchestration Designer surface to configure the orchestration to receive a response message from the Web port.</span></span> <span data-ttu-id="d4d8b-127">如果您連接**接收**圖形至其中一個 Web 連接埠回應訊息連接器，BizTalk 將自動建立自此連接埠接收回應訊息時所要使用的適當類型訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-127">If you connect the **Receive** shape to one of the Web port response message connectors, BizTalk will automatically create a message of the appropriate type to be used when receiving a response message from this port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4d8b-128">使用 SOAP 配接器傳送訊息至 Web 服務，或自 Web 服務接收訊息。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-128">Use the SOAP Adapter to send messages to or receive messages from a Web service.</span></span> <span data-ttu-id="d4d8b-129">如需設定 SOAP 配接器的詳細資訊，請參閱[設定 SOAP 配接器](../core/configuring-the-soap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-129">For more information about configuring the SOAP Adapter see [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md).</span></span>  
  
 <span data-ttu-id="d4d8b-130">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程引擎支援同時使用 Web 服務公開的一維和不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-130">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration Engine provides support for consuming both one dimensional and jagged arrays that are exposed by Web services.</span></span> <span data-ttu-id="d4d8b-131">如果您新增公開陣列之 Web 服務的 Web 參考，則 [協調流程設計師] 將產生描述陣列的 Web 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-131">If you add a Web reference to a Web service that exposes arrays, the Orchestration Designer will generate a Web message type that describes the array.</span></span> <span data-ttu-id="d4d8b-132">然後您就可以傳送和接收此類型的訊息，就像接收其他訊息一般。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-132">You can then send and receive messages of this type like any other message.</span></span> <span data-ttu-id="d4d8b-133">BizTalk Server 不會限制僅傳送包含陣列的 Web 訊息至 Web 連接埠。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-133">BizTalk Server does not limit the sending of Web messages containing arrays to only Web ports.</span></span>  
  
 <span data-ttu-id="d4d8b-134">如需使用 Web 服務陣列的範例，請參閱 SDK 範例 「 取用 Web 服務 」 和 「 取用 Web Services with Array Parameters"網址[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="d4d8b-134">For an example of consuming Web service arrays, see the SDK sample "Consume Web Services" and "Consuming Web Services with Array Parameters" at [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d8b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4d8b-135">See Also</span></span>  
 [<span data-ttu-id="d4d8b-136">協調流程中使用訊息</span><span class="sxs-lookup"><span data-stu-id="d4d8b-136">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)
---
title: 如何新增 Web 連接埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web ports, creating
- creating, Web ports
ms.assetid: da94d98e-10ca-437a-ba34-7aa6efc68f3d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42e9853755788aa29d3ca7506829dcd6bdfed53d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248006"
---
# <a name="how-to-add-a-web-port"></a><span data-ttu-id="4b348-102">如何新增 Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="4b348-102">How to Add a Web Port</span></span>
<span data-ttu-id="4b348-103">您可以使用 [協調流程設計師]，在連接埠介面上新增 Web 連接埠。</span><span class="sxs-lookup"><span data-stu-id="4b348-103">You add a Web port on the port surface in Orchestration Designer.</span></span> <span data-ttu-id="4b348-104">不同於其他已設定的連接埠，Web 連接埠支援混合要求 (單向) 和要求-回應 (雙向) 的作業。</span><span class="sxs-lookup"><span data-stu-id="4b348-104">Unlike other configured ports, Web ports support a mixture of request (one-way) and request/response (two-way) operations.</span></span> <span data-ttu-id="4b348-105">Web 連接埠中的每個作業都代表一個 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="4b348-105">Each operation in the Web port represents a Web method.</span></span> <span data-ttu-id="4b348-106">如果 Web 方法包含*輸入*和*輸出*參數，BizTalk 會建立要求/回應作業。</span><span class="sxs-lookup"><span data-stu-id="4b348-106">If the Web method contains *input* and *output* parameters, BizTalk creates a request/response operation.</span></span> <span data-ttu-id="4b348-107">如果 Web 服務僅包含*輸入*參數，BizTalk 只會建立單向作業。</span><span class="sxs-lookup"><span data-stu-id="4b348-107">If the Web service contains only an *input* parameter, BizTalk only creates a one-way operation.</span></span>  
  
### <a name="to-add-a-web-port"></a><span data-ttu-id="4b348-108">若要新增 Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="4b348-108">To add a Web port</span></span>  
  
1.  <span data-ttu-id="4b348-109">在協調流程設計師中，開啟，協調流程連接埠介面，以滑鼠右鍵按一下，然後選取**新設定連接埠**。</span><span class="sxs-lookup"><span data-stu-id="4b348-109">In Orchestration Designer, with an orchestration open, right-click the port surface, and then select **New Configured Port**.</span></span>  
  
2.  <span data-ttu-id="4b348-110">在 [歡迎使用連接埠組態精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="4b348-110">On the **Welcome to the Port Configuration Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="4b348-111">在**連接埠內容**頁面上，於**名稱** 文字方塊中，輸入連接埠的名稱，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="4b348-111">On the **Port Properties** page, in the **Name** text box, type a name for the port, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="4b348-112">在**選取連接埠類型**頁面上，選取**使用現有的連接埠類型**。</span><span class="sxs-lookup"><span data-stu-id="4b348-112">In the **Select a Port Type** page, select **Use an existing Port Type**.</span></span>  
  
5.  <span data-ttu-id="4b348-113">在**可用的連接埠類型**方塊中，展開  **Web 連接埠類型**節點，然後選取 Web 連接埠來新增 Web 服務中，對應的類型，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="4b348-113">In the **Available Port Types** box, expand the **Web Port Types** node and select the Web port type that corresponds to the added Web service, and then click **Next**.</span></span>  
  
     <span data-ttu-id="4b348-114">下圖顯示**選取連接埠類型** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4b348-114">The following figure shows the **Select a Port Type** dialog box.</span></span>  
  
     ![](../core/media/ebiz-prog-ws-addwebport.gif "ebiz_prog_ws_addwebport")  
  
6.  <span data-ttu-id="4b348-115">在**連接埠繫結**頁面上，於**連接埠繫結**下拉式清單方塊中，選取**現在指定**。</span><span class="sxs-lookup"><span data-stu-id="4b348-115">In the **Port Binding** page, in the **Port binding** drop down box, select **Specify now**.</span></span> <span data-ttu-id="4b348-116">BizTalk 就會自動將參考的 Web 服務提供的值，放在 URI、傳輸，以及接收和傳送管線中。</span><span class="sxs-lookup"><span data-stu-id="4b348-116">BizTalk automatically places the values from the referenced Web service in the URI, transport, and receive and send pipelines.</span></span> <span data-ttu-id="4b348-117">當您部署 BizTalk 專案時，BizTalk 會使用這些值來建立傳送埠。</span><span class="sxs-lookup"><span data-stu-id="4b348-117">BizTalk uses these values to create the send port when you deploy your BizTalk project.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4b348-118">傳送埠的預設驗證方法是匿名存取。</span><span class="sxs-lookup"><span data-stu-id="4b348-118">The default authentication method for the send port is anonymous access.</span></span> <span data-ttu-id="4b348-119">如果 Web 服務需要不同的驗證或加密方法，您必須變更組態，提供適當的使用者認證或安全通訊端層 (SSL) 以執行 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="4b348-119">If the Web service requires a different authentication or encryption method, you must change the configuration to supply the appropriate user credentials or Secure Sockets Layer (SSL) to run Web services.</span></span> <span data-ttu-id="4b348-120">如需詳細資訊，請參閱[SOAP 傳送配接器](../core/soap-send-adapter.md)和[範例 TMA: HTTP 和 SOAP 配接器](../core/sample-tma-http-and-soap-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="4b348-120">For more information, see [SOAP Send Adapter](../core/soap-send-adapter.md) and [Sample TMA: HTTP and SOAP Adapters](../core/sample-tma-http-and-soap-adapters.md).</span></span>  
  
7.  <span data-ttu-id="4b348-121">按一下**下一步**，然後**完成**以完成精靈。</span><span class="sxs-lookup"><span data-stu-id="4b348-121">Click **Next**, and then **Finish** to complete the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b348-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b348-122">See Also</span></span>  
 <span data-ttu-id="4b348-123">[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="4b348-123">[How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md) </span></span>  
 [<span data-ttu-id="4b348-124">建立 Web 連接埠</span><span class="sxs-lookup"><span data-stu-id="4b348-124">Creating Web Ports</span></span>](../core/creating-web-ports.md)
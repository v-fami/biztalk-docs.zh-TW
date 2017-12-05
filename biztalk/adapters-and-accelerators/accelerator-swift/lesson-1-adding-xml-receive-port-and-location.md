---
title: "第 1 課： 將 XML 新增接收埠和位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- receive ports, creating
- creating, receive ports
ms.assetid: 252bc080-3820-44cc-8749-715869f3f684
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d01f9457404e135027f35f1402575efeec311e2e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-1-adding-xml-receive-port-and-location"></a><span data-ttu-id="f1774-102">第 1 課： 加入 XML 接收埠和位置</span><span class="sxs-lookup"><span data-stu-id="f1774-102">Lesson 1: Adding XML Receive Port and Location</span></span>
<span data-ttu-id="f1774-103">接收埠是相似接收位置的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="f1774-103">A receive port is a logical grouping of similar receive locations.</span></span> <span data-ttu-id="f1774-104">接收位置內送訊息，並將用來處理訊息的管線會定義特定位址 （例如 URL 或檔案的位置）。</span><span class="sxs-lookup"><span data-stu-id="f1774-104">A receive location defines a specific address (such as a URL or file location) for an incoming message and the pipeline that is used to process the message.</span></span>  
  
### <a name="to-add-a-receive-port"></a><span data-ttu-id="f1774-105">新增接收埠</span><span class="sxs-lookup"><span data-stu-id="f1774-105">To add a receive port</span></span>  
  
1.  <span data-ttu-id="f1774-106">啟動**BizTalk Server 管理**主控台。</span><span class="sxs-lookup"><span data-stu-id="f1774-106">Start **BizTalk Server Administration** console.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1774-107">BizTalk Server 管理主控台也可以開啟從 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="f1774-107">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="f1774-108">在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理** 節點，然後在**BizTalk 群組** 節點，則**應用程式** 節點，然後**BizTalk Application 1**節點。</span><span class="sxs-lookup"><span data-stu-id="f1774-108">In the BizTalk Server Administration Console, expand the **BizTalk Server Administration** node, then the **BizTalk Group** node, then the **Applications** node, and then the **BizTalk Application 1** node.</span></span>  
  
3.  <span data-ttu-id="f1774-109">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="f1774-109">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="f1774-110">在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入**MT103_XML_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="f1774-110">In the Receive Port Properties dialog box, in the **Name** box, type **MT103_XML_ReceivePort**.</span></span>  
  
5.  <span data-ttu-id="f1774-111">按一下**套用**來繫結連接埠，然後按一下**[確定]。**</span><span class="sxs-lookup"><span data-stu-id="f1774-111">Click **Apply** to bind the port, and then click **OK.**</span></span>  
  
6.  <span data-ttu-id="f1774-112">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="f1774-112">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="f1774-113">在 選取接收埠 對話方塊中，按一下  **MT103_XML_ReceivePort**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f1774-113">In the Select a Receive Port dialog box, click **MT103_XML_ReceivePort**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="f1774-114">在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入**MT103_XML_ReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="f1774-114">In the Receive Location Properties dialog box, in the **Name** box, type **MT103_XML_ReceiveLocation**.</span></span>  
  
9. <span data-ttu-id="f1774-115">在**傳輸** 區段中，針對**類型** 文字方塊中，按一下下拉式清單中，，然後選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="f1774-115">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="f1774-116">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f1774-116">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="f1774-117">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="f1774-117">In the FILE Transport Properties dialog box, click **Browse**.</span></span> <span data-ttu-id="f1774-118">移至**\<磁碟機\>: \Labs**資料夾，然後再按一下**建立新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="f1774-118">Move to the **\<drive\>:\Labs** folder, and then click **Make New Folder**.</span></span>  
  
12. <span data-ttu-id="f1774-119">在 [瀏覽資料夾] 對話方塊中，建立**輸入**資料夾中的**\<磁碟機\>: \Labs**，然後再建立**XMLFile** 中的資料夾**\<磁碟機\>: \Labs\Inbound**。</span><span class="sxs-lookup"><span data-stu-id="f1774-119">In the Browse For Folder dialog box, create an **Inbound** folder in **\<drive\>:\Labs**, and then create an **XMLFile** folder in **\<drive\>:\Labs\Inbound**.</span></span> <span data-ttu-id="f1774-120">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f1774-120">Click **OK**.</span></span>  
  
13. <span data-ttu-id="f1774-121">在 [FILE 傳輸屬性] 對話方塊中，確定 **\*.xml**輸入**檔案遮罩**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f1774-121">In the FILE Transport Properties dialog box, ensure that **\*.xml** is entered in the **File Mask** box, and then click **OK**.</span></span>  
  
14. <span data-ttu-id="f1774-122">在 [接收位置屬性] 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式**方塊。</span><span class="sxs-lookup"><span data-stu-id="f1774-122">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
15. <span data-ttu-id="f1774-123">如**接收管線**方塊中，選取**XMLReceive**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f1774-123">For the **Receive Pipeline** box, select **XMLReceive** from the drop-down list.</span></span>  
  
16. <span data-ttu-id="f1774-124">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f1774-124">Click **Apply**, and then click **OK**.</span></span>  
  
17. <span data-ttu-id="f1774-125">在 BizTalk Server 管理主控台中，按一下 **接收位置**，以滑鼠右鍵按一下**MT103_XML_ReceiveLocation**，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="f1774-125">In the BizTalk Server Administration Console, click **Receive Locations**, right-click **MT103_XML_ReceiveLocation**, and then click **Enable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1774-126">啟用接收位置之後，BizTalk 會主動輪詢檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="f1774-126">After you enable the receive location, BizTalk actively polls your file folder.</span></span>  
  
 <span data-ttu-id="f1774-127">若要繼續[第 2 課： 加入一般檔案傳送埠](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="f1774-127">Proceed to [Lesson 2: Adding the Flat File Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md).</span></span>
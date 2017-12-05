---
title: "第 1 課： 加入一般檔案接收埠和位置 |Microsoft 文件"
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
ms.assetid: 881f58d8-f541-4a85-b534-cb1ca627c002
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9856e0da6e8a4bc958b5fe08e0e1b5e87494531b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-1-adding-flat-file-receive-port-and-location"></a><span data-ttu-id="ac263-102">第 1 課： 加入一般檔案接收埠和位置</span><span class="sxs-lookup"><span data-stu-id="ac263-102">Lesson 1: Adding Flat File Receive Port and Location</span></span>
<span data-ttu-id="ac263-103">接收埠一律會有新增接收埠時，您必須設定相關聯的接收位置。</span><span class="sxs-lookup"><span data-stu-id="ac263-103">The receive port always has an associated receive location that you must configure when you add the receive port.</span></span> <span data-ttu-id="ac263-104">接收位置會定義特定位址的內送訊息和您用來處理訊息的管線。</span><span class="sxs-lookup"><span data-stu-id="ac263-104">A receive location defines a specific address for an incoming message and the pipeline that you use to process the message.</span></span>  
  
### <a name="to-add-a-receive-port"></a><span data-ttu-id="ac263-105">新增接收埠</span><span class="sxs-lookup"><span data-stu-id="ac263-105">To add a receive port</span></span>  
  
1.  <span data-ttu-id="ac263-106">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="ac263-106">In the BizTalk Server Administration Console, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="ac263-107">在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入**MT103_FlatFile_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="ac263-107">In the Receive Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_ReceivePort**.</span></span>  
  
3.  <span data-ttu-id="ac263-108">按一下**套用**來繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ac263-108">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="ac263-109">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="ac263-109">In the BizTalk Server Administration Console, right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
5.  <span data-ttu-id="ac263-110">在 選取接收埠 對話方塊中，按一下  **MT103_FlatFile_ReceivePort**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac263-110">In the Select a Receive Port dialog box, click **MT103_FlatFile_ReceivePort**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="ac263-111">在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入**MT103_FlatFile_ReceiveLocation**。</span><span class="sxs-lookup"><span data-stu-id="ac263-111">In the Receive Location Properties dialog box, in the **Name** box, type **MT103_FlatFile_ReceiveLocation**.</span></span>  
  
7.  <span data-ttu-id="ac263-112">在**傳輸** 區段中，針對**類型** 文字方塊中，按一下下拉式清單中，，然後選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="ac263-112">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
8.  <span data-ttu-id="ac263-113">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ac263-113">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
9. <span data-ttu-id="ac263-114">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="ac263-114">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
10. <span data-ttu-id="ac263-115">在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs\Inbound**資料夾，然後再按一下**建立新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="ac263-115">In the Browse For Folder dialog box, move to the **\<drive\>:\Labs\Inbound** folder, and then click **Make New Folder**.</span></span>  
  
11. <span data-ttu-id="ac263-116">建立**FlatFile**資料夾中的**\<磁碟機\>: \Labs\Inbound**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac263-116">Create a **FlatFile** folder in **\<drive\>:\Labs\Inbound**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="ac263-117">在**檔案遮罩**方塊中，輸入 **\*.txt**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac263-117">In the **File mask** box, type **\*.txt**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="ac263-118">在 [接收位置屬性] 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式**方塊。</span><span class="sxs-lookup"><span data-stu-id="ac263-118">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
14. <span data-ttu-id="ac263-119">如**接收管線**方塊中，選取**MT103ReceivePipeline**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="ac263-119">For the **Receive Pipeline** box, select **MT103ReceivePipeline** from the drop-down list.</span></span>  
  
15. <span data-ttu-id="ac263-120">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ac263-120">Click **Apply**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="ac263-121">在 BizTalk Server 管理主控台中，按一下 **接收位置**，以滑鼠右鍵按一下**MT103_FlatFile_ReceiveLocation**，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="ac263-121">In the BizTalk Server Administration Console, click **Receive Locations**, right-click **MT103_FlatFile_ReceiveLocation**, and then click **Enable**.</span></span>  
  
 <span data-ttu-id="ac263-122">若要繼續[第 2 課： 加入 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="ac263-122">Proceed to [Lesson 2: Adding an XML Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-an-xml-send-port.md).</span></span>
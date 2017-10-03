---
title: "第 2 課： 加入一般檔案傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, flat files
- flat files, send ports
- creating, send ports
- send ports, creating
ms.assetid: 33dceb0d-85f5-4e19-820f-cd33b60cd32a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1370b4877c2e32055e2ee0a0aca1f922bd8668a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-adding-a-flat-file-send-port"></a><span data-ttu-id="736d1-102">第 2 課： 加入一般檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="736d1-102">Lesson 2: Adding a Flat File Send Port</span></span>
<span data-ttu-id="736d1-103">在這一課，您可以設定傳送埠和傳送位置。</span><span class="sxs-lookup"><span data-stu-id="736d1-103">In this lesson, you configure the send port and the send location.</span></span> <span data-ttu-id="736d1-104">您可以使用傳送埠定義您想要傳送訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="736d1-104">You use the send port to define how you want messages sent.</span></span> <span data-ttu-id="736d1-105">您也可以建立傳送訊息的檔案資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="736d1-105">You also create a file folder location for sent messages.</span></span>  
  
### <a name="to-add-a-flat-file-send-port"></a><span data-ttu-id="736d1-106">若要加入一般檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="736d1-106">To add a flat file send port</span></span>  
  
1.  <span data-ttu-id="736d1-107">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="736d1-107">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="736d1-108">在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**MT103_FlatFile_SendPort**。</span><span class="sxs-lookup"><span data-stu-id="736d1-108">In the Send Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_SendPort**.</span></span>  
  
3.  <span data-ttu-id="736d1-109">在**傳輸** 區段中，針對**類型**方塊中，按一下下拉式清單，並選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="736d1-109">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  
  
4.  <span data-ttu-id="736d1-110">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="736d1-110">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
5.  <span data-ttu-id="736d1-111">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="736d1-111">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="736d1-112">在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機 >: \Labs**資料夾，然後再按一下**建立新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="736d1-112">In the Browse For Folder dialog box, move to the **\<drive>:\Labs** folder, and then click **Make New Folder**.</span></span>  
  
7.  <span data-ttu-id="736d1-113">建立**輸出**資料夾中的**\<磁碟機 >: \Labs**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="736d1-113">Create an **Outbound** folder in **\<drive>:\Labs**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="736d1-114">在**檔案名稱**方塊中，輸入**%MessageID%.txt**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="736d1-114">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="736d1-115">在 傳送埠屬性 對話方塊中，按一下 下拉式清單，如**傳送管線**方塊，並選取**MT103SendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="736d1-115">In the Send Port Properties dialog box, click the drop-down list for the **Send pipeline** box, and then select **MT103SendPipeline**.</span></span>  
  
10. <span data-ttu-id="736d1-116">在左窗格中，按一下 **篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="736d1-116">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="736d1-117">使用</span><span class="sxs-lookup"><span data-stu-id="736d1-117">Use this</span></span>|<span data-ttu-id="736d1-118">動作</span><span class="sxs-lookup"><span data-stu-id="736d1-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="736d1-119">**屬性**</span><span class="sxs-lookup"><span data-stu-id="736d1-119">**Property**</span></span>|<span data-ttu-id="736d1-120">選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="736d1-120">Select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="736d1-121">**運算子**</span><span class="sxs-lookup"><span data-stu-id="736d1-121">**Operator**</span></span>|<span data-ttu-id="736d1-122">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="736d1-122">Select **==**.</span></span>|  
    |<span data-ttu-id="736d1-123">**值**</span><span class="sxs-lookup"><span data-stu-id="736d1-123">**Value**</span></span>|<span data-ttu-id="736d1-124">型別**MT103_XML_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="736d1-124">Type **MT103_XML_ReceivePort**.</span></span>|  
  
11. <span data-ttu-id="736d1-125">按一下**套用**，然後按一下  **確定。**</span><span class="sxs-lookup"><span data-stu-id="736d1-125">Click **Apply**, and then click **OK.**</span></span>  
  
12. <span data-ttu-id="736d1-126">在**傳送埠**] 窗格中，以滑鼠右鍵按一下**MT103_FlatFile_SendPort**，然後按一下 [**啟動**。</span><span class="sxs-lookup"><span data-stu-id="736d1-126">In the **Send Ports** pane, right-click **MT103_FlatFile_SendPort**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="736d1-127">若要繼續[模組 5： 加入一般檔案接收位置和 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="736d1-127">Proceed to [Module 5: Adding a Flat File Receive Location and XML Send Port](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md).</span></span>
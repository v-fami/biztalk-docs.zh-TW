---
title: 第 2 課： 加入一般檔案傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, flat files
- flat files, send ports
- creating, send ports
- send ports, creating
ms.assetid: 33dceb0d-85f5-4e19-820f-cd33b60cd32a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90b08dd8083e78d1e7cd98e8e8f705ac23d9bd17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997319"
---
# <a name="lesson-2-adding-a-flat-file-send-port"></a><span data-ttu-id="c5f6e-102">第 2 課： 加入一般檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="c5f6e-102">Lesson 2: Adding a Flat File Send Port</span></span>
<span data-ttu-id="c5f6e-103">在這一課，您可以設定傳送埠和傳送位置。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-103">In this lesson, you configure the send port and the send location.</span></span> <span data-ttu-id="c5f6e-104">您可以使用傳送埠定義您想要傳送訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-104">You use the send port to define how you want messages sent.</span></span> <span data-ttu-id="c5f6e-105">您也會建立傳送訊息的檔案資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-105">You also create a file folder location for sent messages.</span></span>  

### <a name="to-add-a-flat-file-send-port"></a><span data-ttu-id="c5f6e-106">若要新增一般檔案傳送埠</span><span class="sxs-lookup"><span data-stu-id="c5f6e-106">To add a flat file send port</span></span>  

1. <span data-ttu-id="c5f6e-107">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-107">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="c5f6e-108">在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入**MT103_FlatFile_SendPort**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-108">In the Send Port Properties dialog box, in the **Name** box, type **MT103_FlatFile_SendPort**.</span></span>  

3. <span data-ttu-id="c5f6e-109">在**傳輸**區段中，如**型別**方塊中，按一下下拉式清單中，並選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-109">In the **Transport** section, for the **Type** box, click the drop-down list, and then select **FILE**.</span></span>  

4. <span data-ttu-id="c5f6e-110">按一下 **設定**按鈕右邊的 類型 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-110">Click the **Configure** button to the right of the Type drop-down list.</span></span>  

5. <span data-ttu-id="c5f6e-111">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-111">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  

6. <span data-ttu-id="c5f6e-112">在 [瀏覽資料夾] 對話方塊中，移至**\<磁碟機\>: \Labs**資料夾，然後再按一下**建立新資料夾**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-112">In the Browse For Folder dialog box, move to the **\<drive\>:\Labs** folder, and then click **Make New Folder**.</span></span>  

7. <span data-ttu-id="c5f6e-113">建立**Outbound**資料夾中的**\<磁碟機\>: \Labs**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-113">Create an **Outbound** folder in **\<drive\>:\Labs**, and then click **OK**.</span></span>  

8. <span data-ttu-id="c5f6e-114">在 **檔名**方塊中，輸入 **%MessageID%.txt**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-114">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  

9. <span data-ttu-id="c5f6e-115">在傳送埠屬性 對話方塊中，按一下下拉式清單，如**傳送管線**方塊，然後按**MT103SendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-115">In the Send Port Properties dialog box, click the drop-down list for the **Send pipeline** box, and then select **MT103SendPipeline**.</span></span>  

10. <span data-ttu-id="c5f6e-116">在左窗格中，按一下**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="c5f6e-116">In the left pane, click **Filters**, and then do the following:</span></span>  


    |   <span data-ttu-id="c5f6e-117">使用</span><span class="sxs-lookup"><span data-stu-id="c5f6e-117">Use this</span></span>   |           <span data-ttu-id="c5f6e-118">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="c5f6e-118">To do this</span></span>            |
    |--------------|---------------------------------|
    | <span data-ttu-id="c5f6e-119">**屬性**</span><span class="sxs-lookup"><span data-stu-id="c5f6e-119">**Property**</span></span> | <span data-ttu-id="c5f6e-120">選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-120">Select **BTS.ReceivePortName**.</span></span> |
    | <span data-ttu-id="c5f6e-121">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="c5f6e-121">**Operator**</span></span> |         <span data-ttu-id="c5f6e-122">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-122">Select **==**.</span></span>          |
    |  <span data-ttu-id="c5f6e-123">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="c5f6e-123">**Value**</span></span>   | <span data-ttu-id="c5f6e-124">型別**MT103_XML_ReceivePort**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-124">Type **MT103_XML_ReceivePort**.</span></span> |


11. <span data-ttu-id="c5f6e-125">按一下 **套用**，然後按一下  **確定。**</span><span class="sxs-lookup"><span data-stu-id="c5f6e-125">Click **Apply**, and then click **OK.**</span></span>  

12. <span data-ttu-id="c5f6e-126">在 **傳送埠** 窗格中，以滑鼠右鍵按一下**MT103_FlatFile_SendPort**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-126">In the **Send Ports** pane, right-click **MT103_FlatFile_SendPort**, and then click **Start**.</span></span>  

    <span data-ttu-id="c5f6e-127">請繼續進行[模組 5： 新增一般檔案接收位置和 XML 傳送埠](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="c5f6e-127">Proceed to [Module 5: Adding a Flat File Receive Location and XML Send Port](../../adapters-and-accelerators/accelerator-swift/module-5-adding-a-flat-file-receive-location-and-xml-send-port.md).</span></span>
---
title: "建立 A4SWIFT 接收位置 |Microsoft 文件"
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
ms.assetid: 712cf42f-8d71-47e9-b2bf-3da158b74fe4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3f0835c6d83efc9db91f5c1d63e91f4c143399d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-an-a4swift-receive-location"></a><span data-ttu-id="0a4a8-102">建立 A4SWIFT 接收位置</span><span class="sxs-lookup"><span data-stu-id="0a4a8-102">Creating an A4SWIFT Receive Location</span></span>
<span data-ttu-id="0a4a8-103">您必須建立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收位置，才能啟用訊息接收 SWIFT 網路[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-103">You must create an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive location to enable message reception from the SWIFT network by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], as shown in the following figure.</span></span> <span data-ttu-id="0a4a8-104">接收位置接收一般檔案訊息從輸入的檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-104">The receive location receives flat file messages from an inbound file folder.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")  
  
 <span data-ttu-id="0a4a8-105">**摘要**</span><span class="sxs-lookup"><span data-stu-id="0a4a8-105">**Summary**</span></span>  
  
 <span data-ttu-id="0a4a8-106">建立和繫結單向接收埠，然後建立並啟用接收位置具有下列屬性和元件：</span><span class="sxs-lookup"><span data-stu-id="0a4a8-106">Create and bind a one-way receive port, and then create and enable a receive location with the following properties and components:</span></span>  
  
|<span data-ttu-id="0a4a8-107">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="0a4a8-107">Property/Components</span></span>|<span data-ttu-id="0a4a8-108">設定</span><span class="sxs-lookup"><span data-stu-id="0a4a8-108">Setting</span></span>|  
|--------------------------|-------------|  
|<span data-ttu-id="0a4a8-109">接收埠</span><span class="sxs-lookup"><span data-stu-id="0a4a8-109">Receive port</span></span>|<span data-ttu-id="0a4a8-110">單向連接埠</span><span class="sxs-lookup"><span data-stu-id="0a4a8-110">One-way port</span></span>|  
|<span data-ttu-id="0a4a8-111">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="0a4a8-111">Transport type</span></span>|<span data-ttu-id="0a4a8-112">FILE</span><span class="sxs-lookup"><span data-stu-id="0a4a8-112">FILE</span></span>|  
|<span data-ttu-id="0a4a8-113">位址的 URI</span><span class="sxs-lookup"><span data-stu-id="0a4a8-113">Address URI</span></span>|<span data-ttu-id="0a4a8-114">您想要接收訊息的資料夾名稱</span><span class="sxs-lookup"><span data-stu-id="0a4a8-114">Name of the folder that you want to receive the message</span></span>|  
|<span data-ttu-id="0a4a8-115">檔案遮罩</span><span class="sxs-lookup"><span data-stu-id="0a4a8-115">File mask</span></span>|<span data-ttu-id="0a4a8-116">\*.*\<副檔名 >*，其中\<*延伸*> 是個內送的延伸模組一般檔案訊息</span><span class="sxs-lookup"><span data-stu-id="0a4a8-116">\*.*\<extension>*, where \<*extension*> is the extension of the incoming flat file message</span></span>|  
|<span data-ttu-id="0a4a8-117">接收處理常式</span><span class="sxs-lookup"><span data-stu-id="0a4a8-117">Receive handler</span></span>|<span data-ttu-id="0a4a8-118">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="0a4a8-118">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="0a4a8-119">接收管線</span><span class="sxs-lookup"><span data-stu-id="0a4a8-119">Receive pipeline</span></span>|<span data-ttu-id="0a4a8-120">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收您所建立的管線</span><span class="sxs-lookup"><span data-stu-id="0a4a8-120">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created</span></span>|  
  
### <a name="to-add-the-receive-port-and-location"></a><span data-ttu-id="0a4a8-121">若要加入的接收埠和位置</span><span class="sxs-lookup"><span data-stu-id="0a4a8-121">To add the receive port and location</span></span>  
  
1.  <span data-ttu-id="0a4a8-122">啟動**BizTalk Server 管理**主控台。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-122">Start **BizTalk Server Administration** console.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a4a8-123">BizTalk Server 管理主控台也可以開啟從 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-123">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="0a4a8-124">在管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-124">In Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  
  
3.  <span data-ttu-id="0a4a8-125">以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-125">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="0a4a8-126">在 [接收埠屬性] 對話方塊中**名稱**方塊中，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-126">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port.</span></span>  
  
5.  <span data-ttu-id="0a4a8-127">按一下**套用**來繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-127">Click **Apply** to bind the port, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="0a4a8-128">以滑鼠右鍵按一下**接收位置**，指向 **新增**，然後按一下 **單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-128">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="0a4a8-129">在 [選取接收埠] 對話方塊中，按一下您剛才的接收埠建立，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-129">In the Select a Receive Port dialog box, click the receive port that you just created, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="0a4a8-130">在 [接收位置屬性] 對話方塊中**名稱**方塊中，輸入接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-130">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  
  
9. <span data-ttu-id="0a4a8-131">在**傳輸** 區段中，針對**類型** 文字方塊中，按一下下拉式清單中，，然後選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-131">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="0a4a8-132">按一下**設定**按鈕右邊的 [類型] 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-132">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="0a4a8-133">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-133">In the FILE Transport Properties dialog box, click **Browse**.</span></span> <span data-ttu-id="0a4a8-134">您想要接收的訊息移至資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-134">Move to the folder that you want to receive the message.</span></span> <span data-ttu-id="0a4a8-135">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-135">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a4a8-136">如果此資料夾不存在，您可以建立使用**建立新資料夾**命令。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-136">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
12. <span data-ttu-id="0a4a8-137">在 [FILE 傳輸屬性] 對話方塊中**檔案遮罩**方塊中，輸入  **\*。\<*延伸*>**，其中\<*延伸*> 是個內送的延伸模組一般檔案訊息，例如**.txt**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-137">In the FILE Transport Properties dialog box, in the **File Mask** box, enter **\*.\<*extension*>**, where \<*extension*> is the extension of the incoming flat file message, such as **.txt**.</span></span> <span data-ttu-id="0a4a8-138">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-138">Click **OK**.</span></span>  
  
13. <span data-ttu-id="0a4a8-139">在 [接收位置屬性] 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式**方塊。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-139">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
14. <span data-ttu-id="0a4a8-140">如**接收管線**方塊中，從下拉式清單中選取自訂接收管線。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-140">For the **Receive Pipeline** box, select your custom receive pipeline from the drop-down list.</span></span>  
  
15. <span data-ttu-id="0a4a8-141">按一下**套用**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-141">Click **Apply**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="0a4a8-142">在 BizTalk Server 管理主控台中，按一下 **接收位置**，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-142">In the BizTalk Server Administration Console, click **Receive Locations**, right-click the receive location that you just created, and then click **Enable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0a4a8-143">啟用接收位置之後，BizTalk 會主動輪詢檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="0a4a8-143">After you enable the receive location, BizTalk actively polls your file folder.</span></span>
---
title: 建立 A4SWIFT 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
ms.assetid: 712cf42f-8d71-47e9-b2bf-3da158b74fe4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b19330a4d4ab207c7d5e0f920dadb432b733df19
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968367"
---
# <a name="creating-an-a4swift-receive-location"></a><span data-ttu-id="4eabf-102">建立 A4SWIFT 接收位置</span><span class="sxs-lookup"><span data-stu-id="4eabf-102">Creating an A4SWIFT Receive Location</span></span>
<span data-ttu-id="4eabf-103">您必須建立[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收位置，以啟用訊息接收 SWIFT 網路[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="4eabf-103">You must create an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive location to enable message reception from the SWIFT network by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], as shown in the following figure.</span></span> <span data-ttu-id="4eabf-104">接收位置接收一般檔案訊息從輸入的檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4eabf-104">The receive location receives flat file messages from an inbound file folder.</span></span>  

 <span data-ttu-id="4eabf-105">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")</span><span class="sxs-lookup"><span data-stu-id="4eabf-105">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-receive-location-configuration.gif "A4SWIFT_Receive_Location_Configuration")</span></span>  

 <span data-ttu-id="4eabf-106">**摘要**</span><span class="sxs-lookup"><span data-stu-id="4eabf-106">**Summary**</span></span>  

 <span data-ttu-id="4eabf-107">建立和繫結 單向接收埠，然後建立並啟用接收位置具有下列屬性和元件：</span><span class="sxs-lookup"><span data-stu-id="4eabf-107">Create and bind a one-way receive port, and then create and enable a receive location with the following properties and components:</span></span>  


| <span data-ttu-id="4eabf-108">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="4eabf-108">Property/Components</span></span> |                                                             <span data-ttu-id="4eabf-109">設定</span><span class="sxs-lookup"><span data-stu-id="4eabf-109">Setting</span></span>                                                             |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------|
|    <span data-ttu-id="4eabf-110">接收埠</span><span class="sxs-lookup"><span data-stu-id="4eabf-110">Receive port</span></span>     |                                                          <span data-ttu-id="4eabf-111">單向連接埠</span><span class="sxs-lookup"><span data-stu-id="4eabf-111">One-way port</span></span>                                                           |
|   <span data-ttu-id="4eabf-112">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="4eabf-112">Transport type</span></span>    |                                                              <span data-ttu-id="4eabf-113">FILE</span><span class="sxs-lookup"><span data-stu-id="4eabf-113">FILE</span></span>                                                               |
|     <span data-ttu-id="4eabf-114">位址 URI</span><span class="sxs-lookup"><span data-stu-id="4eabf-114">Address URI</span></span>     |                                     <span data-ttu-id="4eabf-115">您想要接收訊息的資料夾名稱</span><span class="sxs-lookup"><span data-stu-id="4eabf-115">Name of the folder that you want to receive the message</span></span>                                     |
|      <span data-ttu-id="4eabf-116">檔案遮罩</span><span class="sxs-lookup"><span data-stu-id="4eabf-116">File mask</span></span>      |                  <span data-ttu-id="4eabf-117">\*.*\<延伸模組\>*，其中\<*延伸模組*\>是延伸模組的內送一般檔案訊息</span><span class="sxs-lookup"><span data-stu-id="4eabf-117">\*.*\<extension\>*, where \<*extension*\> is the extension of the incoming flat file message</span></span>                   |
|   <span data-ttu-id="4eabf-118">接收處理常式</span><span class="sxs-lookup"><span data-stu-id="4eabf-118">Receive handler</span></span>   |                                                    <span data-ttu-id="4eabf-119">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="4eabf-119">BizTalkServerApplication</span></span>                                                     |
|  <span data-ttu-id="4eabf-120">接收管線</span><span class="sxs-lookup"><span data-stu-id="4eabf-120">Receive pipeline</span></span>   | <span data-ttu-id="4eabf-121">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收您所建立的管線</span><span class="sxs-lookup"><span data-stu-id="4eabf-121">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receive pipeline that you created</span></span> |

### <a name="to-add-the-receive-port-and-location"></a><span data-ttu-id="4eabf-122">若要新增接收埠和位置</span><span class="sxs-lookup"><span data-stu-id="4eabf-122">To add the receive port and location</span></span>  

1.  <span data-ttu-id="4eabf-123">開始**BizTalk Server 管理**主控台。</span><span class="sxs-lookup"><span data-stu-id="4eabf-123">Start **BizTalk Server Administration** console.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="4eabf-124">BizTalk Server 管理主控台可以也從開啟 Visual Studio 中依序按一下**BizTalk Server 管理**中**工具**功能表。</span><span class="sxs-lookup"><span data-stu-id="4eabf-124">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  

2.  <span data-ttu-id="4eabf-125">在管理主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-125">In Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand **BizTalk Application 1**.</span></span>  

3.  <span data-ttu-id="4eabf-126">以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-126">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  

4.  <span data-ttu-id="4eabf-127">在接收埠屬性 對話方塊中，在**名稱**方塊中，輸入接收埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="4eabf-127">In the Receive Port Properties dialog box, in the **Name** box, type a name for the receive port.</span></span>  

5.  <span data-ttu-id="4eabf-128">按一下 **套用**要繫結連接埠，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-128">Click **Apply** to bind the port, and then click **OK**.</span></span>  

6.  <span data-ttu-id="4eabf-129">以滑鼠右鍵按一下**接收位置**，指向**新增**，然後按一下**單向接收位置**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-129">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  

7.  <span data-ttu-id="4eabf-130">在 [選取接收埠] 對話方塊中，按一下您剛才的接收埠建立，，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-130">In the Select a Receive Port dialog box, click the receive port that you just created, and then click **OK**.</span></span>  

8.  <span data-ttu-id="4eabf-131">在 [接收位置屬性] 對話方塊中，在**名稱**方塊中，輸入接收位置的名稱。</span><span class="sxs-lookup"><span data-stu-id="4eabf-131">In the Receive Location Properties dialog box, in the **Name** box, type a name for the receive location.</span></span>  

9. <span data-ttu-id="4eabf-132">在**傳輸**區段中，如**型別**文字方塊中，按一下下拉式清單中，然後按**檔案**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-132">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  

10. <span data-ttu-id="4eabf-133">按一下 **設定**按鈕右邊的 類型 下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="4eabf-133">Click the **Configure** button to the right of the Type drop-down list.</span></span>  

11. <span data-ttu-id="4eabf-134">在 [FILE 傳輸屬性] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-134">In the FILE Transport Properties dialog box, click **Browse**.</span></span> <span data-ttu-id="4eabf-135">您想要接收的訊息移至資料夾。</span><span class="sxs-lookup"><span data-stu-id="4eabf-135">Move to the folder that you want to receive the message.</span></span> <span data-ttu-id="4eabf-136">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="4eabf-136">Click **OK**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="4eabf-137">如果此資料夾不存在，您可以使用建立它**建立新資料夾**命令。</span><span class="sxs-lookup"><span data-stu-id="4eabf-137">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  

12. <span data-ttu-id="4eabf-138">在 [FILE 傳輸屬性] 對話方塊中，在**檔案遮罩**方塊中，輸入 **\*。\<*延伸模組*\>**，其中\<*延伸模組*\>是延伸模組的內送一般檔案訊息，例如 **.txt**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-138">In the FILE Transport Properties dialog box, in the **File Mask** box, enter **\*.\<*extension*\>**, where \<*extension*\> is the extension of the incoming flat file message, such as **.txt**.</span></span> <span data-ttu-id="4eabf-139">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="4eabf-139">Click **OK**.</span></span>  

13. <span data-ttu-id="4eabf-140">在 接收位置屬性 對話方塊中，確定**BizTalkServerApplication**輸入**接收處理常式** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="4eabf-140">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  

14. <span data-ttu-id="4eabf-141">針對**接收管線**方塊中，從下拉式清單中選取您的自訂接收管線。</span><span class="sxs-lookup"><span data-stu-id="4eabf-141">For the **Receive Pipeline** box, select your custom receive pipeline from the drop-down list.</span></span>  

15. <span data-ttu-id="4eabf-142">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-142">Click **Apply**, and then click **OK**.</span></span>  

16. <span data-ttu-id="4eabf-143">在 BizTalk Server 管理主控台中，按一下**接收位置**，以滑鼠右鍵按一下您剛才的接收位置建立，，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="4eabf-143">In the BizTalk Server Administration Console, click **Receive Locations**, right-click the receive location that you just created, and then click **Enable**.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="4eabf-144">啟用接收位置之後，BizTalk 會主動輪詢您檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4eabf-144">After you enable the receive location, BizTalk actively polls your file folder.</span></span>
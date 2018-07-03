---
title: 步驟 1： 參考結構描述 DLL2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1db92227-6164-42b9-b60c-12dd2cae46e2
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c58156c64ae9954115ff214518879c4cd17e7417
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984327"
---
# <a name="step-1-reference-the-schema-dll"></a><span data-ttu-id="946e8-102">步驟 1： 參考結構描述 DLL</span><span class="sxs-lookup"><span data-stu-id="946e8-102">Step 1: Reference the Schema DLL</span></span>
<span data-ttu-id="946e8-103">在 BizTalk 中，訊息都是不變的。</span><span class="sxs-lookup"><span data-stu-id="946e8-103">In BizTalk, messages are immutable.</span></span> <span data-ttu-id="946e8-104">因此，若要變更屬性值，您必須建立新訊息並加以修改。</span><span class="sxs-lookup"><span data-stu-id="946e8-104">Therefore, to change a property value you must create and modify a new message.</span></span> <span data-ttu-id="946e8-105">在接收和傳送圖形之間插入訊息指派圖形，就可以建立新訊息和加以修改。</span><span class="sxs-lookup"><span data-stu-id="946e8-105">You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.</span></span>  
  
 <span data-ttu-id="946e8-106">但首先您必須先參考結構描述 DLL，才能取得 J.D.</span><span class="sxs-lookup"><span data-stu-id="946e8-106">First, however, you must reference the schema DLL to gain access to the J.D.</span></span> <span data-ttu-id="946e8-107">Edwards 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="946e8-107">Edwards context properties.</span></span>  
  
### <a name="to-reference-the-schema-dll"></a><span data-ttu-id="946e8-108">若要參考結構描述 DLL</span><span class="sxs-lookup"><span data-stu-id="946e8-108">To reference the schema DLL</span></span>  
  
1. <span data-ttu-id="946e8-109">建立專案的工作資料夾，例如 c:\class\JDE\BeginDoc，以及要置放測試 XML 的資料夾，例如 c:\class\JDE\input。</span><span class="sxs-lookup"><span data-stu-id="946e8-109">Create a working folder, for example, c:\class\JDE\BeginDoc, for your project and a folder in which you will put the test XML, for example, c:\class\JDE\input.</span></span>  
  
2. <span data-ttu-id="946e8-110">建立靜態請求-回應傳送埠傳送要求給 J.D.</span><span class="sxs-lookup"><span data-stu-id="946e8-110">Create a Static Solicit-Response Send Port to send the request to J.D.</span></span> <span data-ttu-id="946e8-111">Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="946e8-111">Edwards OneWorld.</span></span>  
  
    <span data-ttu-id="946e8-112">![](../core/media/jde-example-2waysendport-ow.gif "JDE_example_2waysendport_OW")</span><span class="sxs-lookup"><span data-stu-id="946e8-112">![](../core/media/jde-example-2waysendport-ow.gif "JDE_example_2waysendport_OW")</span></span>  
  
3. <span data-ttu-id="946e8-113">在方案編輯器中，使用滑鼠右鍵按一下專案。</span><span class="sxs-lookup"><span data-stu-id="946e8-113">In the Solution Editor, right-click your project.</span></span>  
  
   1. <span data-ttu-id="946e8-114">選取 **新增**，選取**新增產生的項目**，然後按一下**新增配接器**。</span><span class="sxs-lookup"><span data-stu-id="946e8-114">Select **Add**, select **Add Generated Items**, and then click **Add Adapter**.</span></span>  
  
   2. <span data-ttu-id="946e8-115">選取 Microsoft BizTalk Adapter for J.D.</span><span class="sxs-lookup"><span data-stu-id="946e8-115">Select the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="946e8-116">Edwards OneWorld 和您剛才建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="946e8-116">Edwards OneWorld and the port you just created.</span></span>  
  
   3. <span data-ttu-id="946e8-117">在 **新增配接器精靈**，選取**csales\b4200310**。</span><span class="sxs-lookup"><span data-stu-id="946e8-117">In the **Add Adapter Wizard**, select **CSALES\B4200310**.</span></span>  
  
   4. <span data-ttu-id="946e8-118">按一下 **完成**產生結構描述包含訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="946e8-118">Click **Finish** to generate the schema containing the format for the Message.</span></span>  
  
      <span data-ttu-id="946e8-119">![](../core/media/jde-add-adapter-wizard.gif "JDE_add_adapter_wizard")</span><span class="sxs-lookup"><span data-stu-id="946e8-119">![](../core/media/jde-add-adapter-wizard.gif "JDE_add_adapter_wizard")</span></span>  
  
4. <span data-ttu-id="946e8-120">在 Visual Studio 中，開啟 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="946e8-120">In Visual Studio, open the Solution Explorer.</span></span>  
  
5. <span data-ttu-id="946e8-121">以滑鼠右鍵按一下**參考**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="946e8-121">Right-click **References**, and then select **Add Reference**.</span></span>  
  
6. <span data-ttu-id="946e8-122">在 [**加入參考**畫面上，按一下**瀏覽**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="946e8-122">On the **Add Reference** screen, click the **Browse** button.</span></span>  
  
    <span data-ttu-id="946e8-123">![](../core/media/jde-add-reference-dll.gif "JDE_add_reference_dll")</span><span class="sxs-lookup"><span data-stu-id="946e8-123">![](../core/media/jde-add-reference-dll.gif "JDE_add_reference_dll")</span></span>  
  
7. <span data-ttu-id="946e8-124">在 **選取元件**畫面上，瀏覽至 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。</span><span class="sxs-lookup"><span data-stu-id="946e8-124">On the **Select Component** screen, navigate to %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span></span>  
  
8. <span data-ttu-id="946e8-125">選取  **microsoft.adapters.jdeproperties.dll**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="946e8-125">Select **Microsoft.Adapters.JDEProperties.dll**, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="946e8-126">在上**加入參考**畫面中，此 DLL 會出現在**選取的元件**一節。</span><span class="sxs-lookup"><span data-stu-id="946e8-126">On the **Add Reference** screen, the DLL appears in the **Selected Components** section.</span></span>  
  
     <span data-ttu-id="946e8-127">![](../core/media/jde-properties-selection.gif "JDE_properties_selection")</span><span class="sxs-lookup"><span data-stu-id="946e8-127">![](../core/media/jde-properties-selection.gif "JDE_properties_selection")</span></span>  
  
10. <span data-ttu-id="946e8-128">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="946e8-128">Click **OK**.</span></span>  
  
11. <span data-ttu-id="946e8-129">按兩下協調流程來存取協調流程設計師。</span><span class="sxs-lookup"><span data-stu-id="946e8-129">Double-click your orchestration to access the Orchestration Designer.</span></span>  
  
     <span data-ttu-id="946e8-130">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="946e8-130">\- OR -</span></span>  
  
     <span data-ttu-id="946e8-131">選取 **檢視**，選取**其他 Windows**，然後按一下**協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="946e8-131">Select **View**, select **Other Windows**, and then click **Orchestration View**.</span></span>  
  
     <span data-ttu-id="946e8-132">[協調流程檢視] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="946e8-132">The Orchestration View appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946e8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="946e8-133">See Also</span></span>  
 <span data-ttu-id="946e8-134">[步驟 2： 建立協調流程](../core/step-2-create-the-orchestration1.md) </span><span class="sxs-lookup"><span data-stu-id="946e8-134">[Step 2: Create the Orchestration](../core/step-2-create-the-orchestration1.md) </span></span>  
 <span data-ttu-id="946e8-135">[步驟 3： 完成及執行專案](../core/step-3-complete-and-run-the-project2.md) </span><span class="sxs-lookup"><span data-stu-id="946e8-135">[Step 3: Complete and Run the Project](../core/step-3-complete-and-run-the-project2.md) </span></span>  
 [<span data-ttu-id="946e8-136">步驟 4：建立範例 XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="946e8-136">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc1.md)
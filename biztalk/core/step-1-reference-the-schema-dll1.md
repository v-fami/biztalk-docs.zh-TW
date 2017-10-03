---
title: "步驟 1： 參考結構描述 DLL1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47e4b773-e484-4931-9ab2-b8dd0080ea1c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c2d5051c7dfd3c0f971b34922ca4e5747117c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-reference-the-schema-dll"></a><span data-ttu-id="27f2a-102">步驟 1： 參考結構描述 DLL</span><span class="sxs-lookup"><span data-stu-id="27f2a-102">Step 1: Reference the Schema DLL</span></span>
<span data-ttu-id="27f2a-103">在 BizTalk 中，訊息都是不變的。</span><span class="sxs-lookup"><span data-stu-id="27f2a-103">In BizTalk, messages are immutable.</span></span> <span data-ttu-id="27f2a-104">因此，若要變更屬性值，您必須建立新訊息並加以修改。</span><span class="sxs-lookup"><span data-stu-id="27f2a-104">Therefore, to change a property value you must create and modify a new message.</span></span> <span data-ttu-id="27f2a-105">在接收和傳送圖形之間插入訊息指派圖形，就可以建立新訊息和加以修改。</span><span class="sxs-lookup"><span data-stu-id="27f2a-105">You create and modify the new message by inserting a message assignment shape between the Receive and Send shapes.</span></span>  
  
 <span data-ttu-id="27f2a-106">但首先您必須先參考結構描述 DLL，才能取得 J.D.</span><span class="sxs-lookup"><span data-stu-id="27f2a-106">First, however, you must reference the schema DLL to gain access to the J.D.</span></span> <span data-ttu-id="27f2a-107">Edwards EnterpriseOne 內容屬性的存取權。</span><span class="sxs-lookup"><span data-stu-id="27f2a-107">Edwards EnterpriseOne context properties.</span></span>  
  
### <a name="to-reference-the-schema-dll"></a><span data-ttu-id="27f2a-108">若要參考結構描述 DLL</span><span class="sxs-lookup"><span data-stu-id="27f2a-108">To reference the schema DLL</span></span>  
  
1.  <span data-ttu-id="27f2a-109">建立專案的工作資料夾，例如 c:\class\JDE\BeginDoc，以及要置放測試 XML 的資料夾，例如 c:\class\JDE\input。</span><span class="sxs-lookup"><span data-stu-id="27f2a-109">Create a working folder, for example, c:\class\JDE\BeginDoc, for your project and a folder in which you will put the test XML, for example, c:\class\JDE\input.</span></span>  
  
2.  <span data-ttu-id="27f2a-110">建立靜態請求-回應傳送埠傳送要求給 J.D.</span><span class="sxs-lookup"><span data-stu-id="27f2a-110">Create a Static Solicit-Response Send Port to send the request to J.D.</span></span> <span data-ttu-id="27f2a-111">Edwards EnterpriseOne。</span><span class="sxs-lookup"><span data-stu-id="27f2a-111">Edwards EnterpriseOne.</span></span>  
  
     <span data-ttu-id="27f2a-112">![JDOneWorld 傳輸屬性](../core/media/example-2waysendport-ow.gif "example_2waysendport_OW")</span><span class="sxs-lookup"><span data-stu-id="27f2a-112">![JDOneWorld Transport Properties](../core/media/example-2waysendport-ow.gif "example_2waysendport_OW")</span></span>  
  
3.  <span data-ttu-id="27f2a-113">在方案編輯器中，使用滑鼠右鍵按一下專案。</span><span class="sxs-lookup"><span data-stu-id="27f2a-113">In the Solution Editor, right-click your project.</span></span>  
  
    1.  <span data-ttu-id="27f2a-114">選取**新增**，選取**新增產生的項目**，然後按一下 **新增配接器**。</span><span class="sxs-lookup"><span data-stu-id="27f2a-114">Select **Add**, select **Add Generated Items**, and then click **Add Adapter**.</span></span>  
  
    2.  <span data-ttu-id="27f2a-115">選取 Microsoft BizTalk Adapter for J.D.</span><span class="sxs-lookup"><span data-stu-id="27f2a-115">Select the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="27f2a-116">Edwards EnterpriseOne 以及您剛才建立的連接埠。</span><span class="sxs-lookup"><span data-stu-id="27f2a-116">Edwards EnterpriseOne and the port you just created.</span></span>  
  
    3.  <span data-ttu-id="27f2a-117">在**新增配接器精靈**，選取**[csales\b4200310]**。</span><span class="sxs-lookup"><span data-stu-id="27f2a-117">In the **Add Adapter Wizard**, select **CSALES\B4200310**.</span></span>  
  
    4.  <span data-ttu-id="27f2a-118">按一下**完成**產生結構描述包含訊息的格式。</span><span class="sxs-lookup"><span data-stu-id="27f2a-118">Click **Finish** to generate the schema containing the format for the Message.</span></span>  
  
     <span data-ttu-id="27f2a-119">![新增配接器精靈](../core/media/add-adapter-wizard.gif "add_adapter_wizard")</span><span class="sxs-lookup"><span data-stu-id="27f2a-119">![Add Adapter Wizard](../core/media/add-adapter-wizard.gif "add_adapter_wizard")</span></span>  
  
4.  <span data-ttu-id="27f2a-120">在 Visual Studio 中，開啟 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="27f2a-120">In Visual Studio, open the Solution Explorer.</span></span>  
  
5.  <span data-ttu-id="27f2a-121">以滑鼠右鍵按一下**參考**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="27f2a-121">Right-click **References**, and then select **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="27f2a-122">在**加入參考**畫面上，按一下**瀏覽** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="27f2a-122">On the **Add Reference** screen, click the **Browse** button.</span></span>  
  
7.  <span data-ttu-id="27f2a-123">在**選取元件**畫面上，瀏覽至 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。</span><span class="sxs-lookup"><span data-stu-id="27f2a-123">On the **Select Component** screen, navigate to %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.</span></span>  
  
8.  <span data-ttu-id="27f2a-124">選取**microsoft.adapters.jdeproperties.dll**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="27f2a-124">Select **Microsoft.Adapters.JDEProperties.dll**, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="27f2a-125">在**加入參考** 畫面上，此 DLL 會出現在**選取的元件**> 一節。</span><span class="sxs-lookup"><span data-stu-id="27f2a-125">On the **Add Reference** screen, the DLL appears in the **Selected Components** section.</span></span>  
  
     <span data-ttu-id="27f2a-126">![屬性選取畫面](../core/media/properties-selection.gif "properties_selection")</span><span class="sxs-lookup"><span data-stu-id="27f2a-126">![Properties Selection screen](../core/media/properties-selection.gif "properties_selection")</span></span>  
  
10. <span data-ttu-id="27f2a-127">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="27f2a-127">Click **OK**.</span></span>  
  
11. <span data-ttu-id="27f2a-128">按兩下協調流程來存取協調流程設計師。</span><span class="sxs-lookup"><span data-stu-id="27f2a-128">Double-click your orchestration to access the Orchestration Designer.</span></span>  
  
     <span data-ttu-id="27f2a-129">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="27f2a-129">\- OR -</span></span>  
  
     <span data-ttu-id="27f2a-130">選取**檢視**，選取**其他視窗**，然後按一下 **協調流程檢視**。</span><span class="sxs-lookup"><span data-stu-id="27f2a-130">Select **View**, select **Other Windows**, and then click **Orchestration View**.</span></span>  
  
     <span data-ttu-id="27f2a-131">[協調流程檢視] 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="27f2a-131">The Orchestration View appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f2a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27f2a-132">See Also</span></span>  
 <span data-ttu-id="27f2a-133">[步驟 2： 建立協調流程](../core/step-2-create-the-orchestration2.md) </span><span class="sxs-lookup"><span data-stu-id="27f2a-133">[Step 2: Create the Orchestration](../core/step-2-create-the-orchestration2.md) </span></span>  
 <span data-ttu-id="27f2a-134">[工作 4： 設定建構訊息圖形](../core/task-4-configure-the-construct-message-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="27f2a-134">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md) </span></span>  
 <span data-ttu-id="27f2a-135">[工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape2.md) </span><span class="sxs-lookup"><span data-stu-id="27f2a-135">[Task 5: Configure the Transform Shape](../core/task-5-configure-the-transform-shape2.md) </span></span>  
 <span data-ttu-id="27f2a-136">[步驟 3： 完成及執行專案](../core/step-3-complete-and-run-the-project1.md) </span><span class="sxs-lookup"><span data-stu-id="27f2a-136">[Step 3: Complete and Run the Project](../core/step-3-complete-and-run-the-project1.md) </span></span>  
 [<span data-ttu-id="27f2a-137">步驟 4： 建立範例 XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="27f2a-137">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc2.md)
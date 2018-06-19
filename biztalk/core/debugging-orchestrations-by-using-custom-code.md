---
title: 使用自訂程式碼偵錯協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, debugging
- building, debugging
ms.assetid: 94e569fa-8dea-4027-abb5-37b4a8015621
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47f69fa635a90db90c461f75c300334ccc499b94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239886"
---
# <a name="debugging-orchestrations-by-using-custom-code"></a><span data-ttu-id="17125-102">使用自訂程式碼偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="17125-102">Debugging Orchestrations by using Custom Code</span></span>
<span data-ttu-id="17125-103">如果您的協調流程會在測試環境中執行，或您正在建立原型並想要修改訊息欄位和協調流程變數的值，您可以將輸出寫入[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]主控台中使用下列程式碼**運算式**圖形：</span><span class="sxs-lookup"><span data-stu-id="17125-103">If your orchestration is going to be exercised in a test environment or you are creating a prototype and want to modify the values of message fields and orchestration variables, you can write the output to the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] console by using the following code in an **Expression** shape:</span></span>  
  
```  
System.Diagnostics.Debug.WriteLine(iResult);  
```  
  
 <span data-ttu-id="17125-104">您需要將此**運算式**立即執行作業，以便您可以將結果輸出進行偵錯的圖形之後的圖形。</span><span class="sxs-lookup"><span data-stu-id="17125-104">You need to place this **Expression** shape immediately after the shape that performs the operation so that you can output the result for debugging.</span></span>  
  
 <span data-ttu-id="17125-105">或者，您也可以建立偵錯 DLL，撰寫簡單的自訂偵錯工具，在這個偵錯 DLL 裡所用的類別必須可以將輸入視為訊息，而且這個訊息的格式必須已在協調流程中定義並為偵錯 DLL 所參考。</span><span class="sxs-lookup"><span data-stu-id="17125-105">Alternatively, you can write a simple custom debugger by creating a debugging DLL with a class that includes a method which takes as input a message with a format defined in your orchestration and referenced in the debug DLL.</span></span> <span data-ttu-id="17125-106">如需傳遞訊息做為參數的詳細資訊，請參閱[如何使用運算式建立物件和呼叫物件方法](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="17125-106">For more information about passing a message as a parameter, see [How to Use Expressions to Create Objects and Call Object Methods](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md).</span></span>  
  
 <span data-ttu-id="17125-107">此方法會顯示具有下拉式方塊或其他控制項的對話方塊，可讓使用者修改值，然後將編輯好的訊息放在一起，並傳回為傳回值。</span><span class="sxs-lookup"><span data-stu-id="17125-107">This method can bring up a debug dialog that includes a combo box or other control to allow user modification of values, puts the edited message back together, and passes it back out as the return value.</span></span>  
  
 <span data-ttu-id="17125-108">設定布林值變數，表示您的協調流程是否處於偵錯模式，則只要您有一個點您想要能夠修改值的協調流程中，您可以加入**決定**有一個即時圖形只有當您偵錯模式變數設為 True，或是當您想要檢查的特定條件發生時執行的分支。</span><span class="sxs-lookup"><span data-stu-id="17125-108">Set up a Boolean variable to indicate whether or not your orchestration is in debug mode, then wherever you have a point in your orchestration at which you would like to be able to modify values, you can add a **Decide** shape with one live branch that runs only when your debug mode variable is set to True, or when a particular condition arises that you want to examine.</span></span> <span data-ttu-id="17125-109">呼叫您的方法，從**運算式**圖形中的即時分支**決定**。</span><span class="sxs-lookup"><span data-stu-id="17125-109">You call your method from an **Expression** shape in the live branch of the **Decide**.</span></span> <span data-ttu-id="17125-110">當您不再需要偵錯時，偵錯模式變數設為 False，或移除**決定**圖形完全並重新編譯。</span><span class="sxs-lookup"><span data-stu-id="17125-110">When you no longer need to debug, you set your debug mode variable to False, or remove the **Decide** shape(s) altogether and recompile.</span></span>  
  
## <a name="to-debug-a-net-component-called-by-an-orchestration"></a><span data-ttu-id="17125-111">偵錯協調流程呼叫的 .NET 元件</span><span class="sxs-lookup"><span data-stu-id="17125-111">To Debug a .NET component called by an Orchestration</span></span>  
 <span data-ttu-id="17125-112">下列步驟示範如何偵錯協調流程呼叫的 .NET 元件：</span><span class="sxs-lookup"><span data-stu-id="17125-112">The following steps demonstrate how to debug a .NET component called by an Orchestration:</span></span>  
  
1.  <span data-ttu-id="17125-113">開啟元件的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="17125-113">Open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for your component.</span></span>  
  
2.  <span data-ttu-id="17125-114">在協調流程呼叫的方法上設定您元件的中斷點。</span><span class="sxs-lookup"><span data-stu-id="17125-114">Set a breakpoint in your component on the method that is called by the orchestration.</span></span>  
  
3.  <span data-ttu-id="17125-115">按一下**偵錯**功能表，然後選取**附加至處理序...**</span><span class="sxs-lookup"><span data-stu-id="17125-115">Click the **Debug** menu and select **Attach to Process…**</span></span> <span data-ttu-id="17125-116">若要顯示**附加至處理序**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="17125-116">to display the **Attach to Process** dialog.</span></span>  
  
4.  <span data-ttu-id="17125-117">按一下**選取...**</span><span class="sxs-lookup"><span data-stu-id="17125-117">Click the **Select…**</span></span> <span data-ttu-id="17125-118">下一步按鈕**附加至：** 文字方塊中，以顯示**選取程式碼類型**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="17125-118">button next to the **Attach to:** text box to display the **Select Code Type** dialog.</span></span>  
  
5.  <span data-ttu-id="17125-119">按一下以選取的選項**偵錯這些程式碼類型：** 並選取**Managed** ，然後按一下 **確定**按鈕。</span><span class="sxs-lookup"><span data-stu-id="17125-119">Click to select the option to **Debug these code types:** and select **Managed** and then click the **OK** button.</span></span>  
  
6.  <span data-ttu-id="17125-120">按一下以選取**BTSNTSvc.exe**處理序**可用的處理序**，然後按一下 [**附加**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="17125-120">Click to select the **BTSNTSvc.exe** process from **Available Processes** and then click the **Attach** button.</span></span>  
  
7.  <span data-ttu-id="17125-121">透過接收埠將訊息傳送到您的協調流程。</span><span class="sxs-lookup"><span data-stu-id="17125-121">Send a message to your orchestration through a receive port.</span></span>  
  
8.  <span data-ttu-id="17125-122">.NET 元件應該在中斷點上停止。</span><span class="sxs-lookup"><span data-stu-id="17125-122">The .NET component should be stopped in the breakpoint.</span></span>  
  
9. <span data-ttu-id="17125-123">您可以跟平常一樣使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 執行偵錯。</span><span class="sxs-lookup"><span data-stu-id="17125-123">You can perform debugging as usual with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="17125-124">若要取得最佳結果，應該在全域組件快取 (GAC) 中註冊 .NET 元件。</span><span class="sxs-lookup"><span data-stu-id="17125-124">For best results, the .NET component should be registered in the Global Assembly Cache (GAC).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17125-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17125-125">See Also</span></span>  
 <span data-ttu-id="17125-126">[協調流程偵錯工具使用者介面](../core/orchestration-debugger-user-interface.md) </span><span class="sxs-lookup"><span data-stu-id="17125-126">[Orchestration Debugger User Interface](../core/orchestration-debugger-user-interface.md) </span></span>  
 [<span data-ttu-id="17125-127">偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="17125-127">Debugging Orchestrations</span></span>](../core/debugging-orchestrations.md)
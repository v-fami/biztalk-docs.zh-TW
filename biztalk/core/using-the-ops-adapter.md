---
title: 使用 Ops 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IOpsAIC interface
- Ops adapters, configuring
- Ops adapters, IOpsAIC interface
- process management solution tutorial, Ops adapters
- Ops adapters, processing
ms.assetid: 331f3614-e00b-4587-b82b-3c7bc394f361
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d93436e727265c4b381cdff72c42b3a677d0a4dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288734"
---
# <a name="using-the-ops-adapter"></a><span data-ttu-id="90218-102">使用 Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="90218-102">Using the Ops Adapter</span></span>
<span data-ttu-id="90218-103">商務程序管理解決方案使用 Ops 配接器處理來自新錯誤報告功能的錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="90218-103">The business process management solution uses the Ops adapter to handle error reports from the new error reporting feature.</span></span> <span data-ttu-id="90218-104">解決方案包括一個處理配接器訊息的範例處理常式，但您可以輕鬆的撰寫自己的處理常式，並使用其他解決方案中的配接器。</span><span class="sxs-lookup"><span data-stu-id="90218-104">The solution includes a sample handler to process messages from the adapter, although you can easily write your own and use the adapter in other solutions.</span></span> <span data-ttu-id="90218-105">錯誤報告功能的相關資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。</span><span class="sxs-lookup"><span data-stu-id="90218-105">For information about the error reporting feature, see [Using Failed Message Routing](../core/using-failed-message-routing.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90218-106">雖然解決方案使用配接器處理錯誤報告，但配接器的用途不僅限於錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="90218-106">Although the solution uses the adapter for error reporting, its use is not limited to error handling.</span></span> <span data-ttu-id="90218-107">您可以在執行特定物件方法以回應訊息的各種不同狀況中使用配接器。</span><span class="sxs-lookup"><span data-stu-id="90218-107">You can use the adapter in a variety of circumstances whenever you want to execute a specific object method in response to a message.</span></span>  
  
## <a name="how-the-ops-adapter-processes-error-reports"></a><span data-ttu-id="90218-108">Ops 配接器如何處理錯誤報告</span><span class="sxs-lookup"><span data-stu-id="90218-108">How the Ops Adapter Processes Error Reports</span></span>  
 <span data-ttu-id="90218-109">在方案中使用錯誤報告的連接埠最後會傳送錯誤訊息，以**BIZTALKERRORS-SP**連接埠。</span><span class="sxs-lookup"><span data-stu-id="90218-109">Ports in the solution that use error reporting ultimately send the error messages to the **BizTalkErrors-SP** port.</span></span> <span data-ttu-id="90218-110">連接埠篩選條件會測試是否存在**ErrorReport.ErrorType**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="90218-110">The filter on the port tests for the existence of the **ErrorReport.ErrorType** context property.</span></span> <span data-ttu-id="90218-111">只有錯誤報告訊息擁有此內容屬性。</span><span class="sxs-lookup"><span data-stu-id="90218-111">Only error report messages have this context property.</span></span>  
  
 <span data-ttu-id="90218-112">**BIZTALKERRORS-SP**傳送連接埠會透過使用 XML 組合器元件將訊息放置在信封中的管線執行錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-112">The **BizTalkErrors-SP** send port runs the error message through a pipeline that uses an XML assembler component to put the message in an envelope.</span></span> <span data-ttu-id="90218-113">然後訊息移至 Ops 配接器。</span><span class="sxs-lookup"><span data-stu-id="90218-113">The message then goes to the Ops adapter.</span></span>  
  
 <span data-ttu-id="90218-114">ErrorEnvelope 結構描述所定義的信封標示為可接受任何類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-114">The envelope, defined by the ErrorEnvelope schema, is marked to accept any type of message.</span></span> <span data-ttu-id="90218-115">但 "any" 表示 BizTalk 群組中所定義的任何訊息類型。</span><span class="sxs-lookup"><span data-stu-id="90218-115">However, "any" means any message type defined in the BizTalk group.</span></span> <span data-ttu-id="90218-116">若解決方案收到未知類型的訊息，便會產生擱置的訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-116">This can produce suspended messages if the solution receives a message of an unknown type.</span></span> <span data-ttu-id="90218-117">這類訊息會產生錯誤，就會路由至**BIZTALKERRORS-SP**連接埠。</span><span class="sxs-lookup"><span data-stu-id="90218-117">Such a message would produce an error and would be routed to the **BizTalkErrors-SP** port.</span></span> <span data-ttu-id="90218-118">然後，訊息會在管線的 XML 組合器元件中產生錯誤，因為它不是已知的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="90218-118">In turn, the message would generate an error in the XML assembler component of the pipeline because it would not be a known message type.</span></span> <span data-ttu-id="90218-119">管線錯誤會擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-119">The pipeline error suspends the message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90218-120">若要處理未知的訊息類型導致的路由錯誤，您必須撰寫自訂管線元件，並使用中的自訂管線元件**BIZTALKERRORS-SP**連接埠。</span><span class="sxs-lookup"><span data-stu-id="90218-120">To handle routing errors due to unknown message types, you must write a custom pipeline component and use the component in a custom pipeline for the **BizTalkErrors-SP** port.</span></span> <span data-ttu-id="90218-121">自訂元件會取代 XML 組合器元件。</span><span class="sxs-lookup"><span data-stu-id="90218-121">The custom component replaces the XML assembler component.</span></span> <span data-ttu-id="90218-122">您的自訂元件必須將**ErrorReport**信封標頭中的屬性並將訊息加入至 envelope 的主體。</span><span class="sxs-lookup"><span data-stu-id="90218-122">Your custom component must put the **ErrorReport** properties in the envelope header and add the message to the body of the envelope.</span></span>  
  
 <span data-ttu-id="90218-123">Ops 配接器是交易式的單向傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="90218-123">The Ops adapter is a transactional, one-way send adapter.</span></span> <span data-ttu-id="90218-124">配接器處理訊息時，若有必要，會先載入指定的組件。</span><span class="sxs-lookup"><span data-stu-id="90218-124">When the adapter processes a message, it first loads the specified assembly, if necessary.</span></span> <span data-ttu-id="90218-125">配接器將組件快取在記憶體中，以避免載入各呼叫組件的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="90218-125">The adapter caches assemblies in memory to avoid the overhead of loading the assembly for each call.</span></span> <span data-ttu-id="90218-126">它接著會建立指定類別的執行個體，然後再使用反映取得的物件中實作的組件**IOpsAIC**介面。</span><span class="sxs-lookup"><span data-stu-id="90218-126">It then creates an instance of the specified class, and then uses reflection to get the object in the assembly implementing the **IOpsAIC** interface.</span></span> <span data-ttu-id="90218-127">如果全部都成功，配接器會呼叫**初始化**方法，然後呼叫**Execute**方法，傳遞錯誤報告訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-127">If all of this is successful, the adapter calls the **Initialize** method and then calls the **Execute** method, passing the error report message.</span></span>  
  
 <span data-ttu-id="90218-128">如果錯誤呼叫**Execute**，配接器重新提交訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-128">If there is an error calling **Execute**, the adapter resubmits the message.</span></span> <span data-ttu-id="90218-129">如果指定的類別未實作**IOpsAIC**找不到介面或類別或組件，配接器會擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="90218-129">If the specified class does not implement the **IOpsAIC** interface, or the class or assembly can't be found, the adapter suspends the message.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="90218-130">因為配接器使用反映，包含類別的組件必須位於全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="90218-130">Because the adapter uses reflection, the assembly containing the class must be in the Global Assembly Cache (GAC).</span></span>  
  
## <a name="the-iopsaic-interface"></a><span data-ttu-id="90218-131">IOpsAIC 介面</span><span class="sxs-lookup"><span data-stu-id="90218-131">The IOpsAIC Interface</span></span>  
 <span data-ttu-id="90218-132">配接器需要實作的物件**IOpsAIC**介面。</span><span class="sxs-lookup"><span data-stu-id="90218-132">The adapter requires an object that implements the **IOpsAIC** interface.</span></span> <span data-ttu-id="90218-133">介面顯示如下：</span><span class="sxs-lookup"><span data-stu-id="90218-133">The interface appears as follows:</span></span>  
  
```  
interface IOpsAIC  
{  
    void Initialize(string config);  
    void Execute(byte[] message);  
}  
```  
  
 <span data-ttu-id="90218-134">配接器會將原始訊息傳遞為位元組陣列**Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="90218-134">The adapter passes the original message as a byte array to the **Execute** method.</span></span>  
  
## <a name="configuring-the-adapter"></a><span data-ttu-id="90218-135">設定配接器</span><span class="sxs-lookup"><span data-stu-id="90218-135">Configuring the Adapter</span></span>  
 <span data-ttu-id="90218-136">設定此配接器的方法和設定其他配接器的方法相同。</span><span class="sxs-lookup"><span data-stu-id="90218-136">You configure the adapter just as you would any other adapter.</span></span> <span data-ttu-id="90218-137">下表描述配接器的組態屬性：</span><span class="sxs-lookup"><span data-stu-id="90218-137">The following table describes the adapter's configuration properties:</span></span>  
  
|<span data-ttu-id="90218-138">顯示名稱</span><span class="sxs-lookup"><span data-stu-id="90218-138">Display Name</span></span>|<span data-ttu-id="90218-139">Description</span><span class="sxs-lookup"><span data-stu-id="90218-139">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="90218-140">**.NET 組件強式名稱**</span><span class="sxs-lookup"><span data-stu-id="90218-140">**.NET Assembly Strong Name**</span></span>|<span data-ttu-id="90218-141">組件的完整格式名稱。</span><span class="sxs-lookup"><span data-stu-id="90218-141">The fully qualified name of the assembly.</span></span>|  
|<span data-ttu-id="90218-142">**OpsAIC 類別名稱**</span><span class="sxs-lookup"><span data-stu-id="90218-142">**OpsAIC Class Name**</span></span>|<span data-ttu-id="90218-143">實作的組件內的類別名稱**IOpsAIC**介面。</span><span class="sxs-lookup"><span data-stu-id="90218-143">The name of the class within the assembly that implements the **IOpsAIC** interface.</span></span>|  
|<span data-ttu-id="90218-144">**初始化資料**</span><span class="sxs-lookup"><span data-stu-id="90218-144">**Initialization Data**</span></span>|<span data-ttu-id="90218-145">做為引數傳遞的字串**初始化**類別的方法。</span><span class="sxs-lookup"><span data-stu-id="90218-145">A string passed as an argument to the **Initialize** method of the class.</span></span>|  
  
 <span data-ttu-id="90218-146">請注意，配接器需要有組件的完整格式名稱。</span><span class="sxs-lookup"><span data-stu-id="90218-146">Notice that the adapter requires the fully qualified name of the assembly.</span></span> <span data-ttu-id="90218-147">完整格式名稱是您將組件新增至 GAC 時所指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="90218-147">The fully qualified name is the name given to an assembly when you add it to the GAC.</span></span> <span data-ttu-id="90218-148">完整格式名稱是包含組件名稱、版本、文化特性、公開金鑰 Token 的字串。</span><span class="sxs-lookup"><span data-stu-id="90218-148">The fully qualified name is a string containing the assembly's name, version, culture, and public key token.</span></span> <span data-ttu-id="90218-149">您可以使用全域組件快取工具 gacutil.exe 查看組件的完整格式名稱。</span><span class="sxs-lookup"><span data-stu-id="90218-149">You can see the fully qualified names of assemblies by using the Global Assembly Cache Tool, gacutil.exe.</span></span>  
  
 <span data-ttu-id="90218-150">如需有關完整格式組件名稱的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的＜組件名稱＞。</span><span class="sxs-lookup"><span data-stu-id="90218-150">For more information about fully qualified assembly names, see "Assembly Names" in the .NET Framework Developer's Guide.</span></span> <span data-ttu-id="90218-151">如需有關 gacutil.exe 的詳細資訊，請參閱《[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 開發人員手冊》中的＜全域組件快取工具 (Gacutil.exe)＞。</span><span class="sxs-lookup"><span data-stu-id="90218-151">For more information about gacutil.exe, see "Global Assembly Cache Tool (Gacutil.exe)" in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Developer's Guide.</span></span>  
  
 <span data-ttu-id="90218-152">您必須在類別名稱提供命名空間。</span><span class="sxs-lookup"><span data-stu-id="90218-152">You must provide the namespace with the class name.</span></span> <span data-ttu-id="90218-153">例如，如果類別為**OpsHandler**中**OperationsHandler**命名空間，您會將類別命名做為**OperationsHandler.OpsHandler**。</span><span class="sxs-lookup"><span data-stu-id="90218-153">For example, if the class is **OpsHandler** in the **OperationsHandler** namespace, you would give the class name as **OperationsHandler.OpsHandler**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90218-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90218-154">See Also</span></span>  
 [<span data-ttu-id="90218-155">Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="90218-155">The Ops Adapter</span></span>](../core/the-ops-adapter.md)
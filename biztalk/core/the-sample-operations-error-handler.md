---
title: "範例作業錯誤處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Ops adapters, error handler
- process management solution tutorial, Ops adapters
ms.assetid: e6c55f01-c004-4340-beaa-d77764ae34c1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93536733c884b4d5db57ba18619ebabdead17561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-sample-operations-error-handler"></a><span data-ttu-id="69257-102">範例作業錯誤處理常式</span><span class="sxs-lookup"><span data-stu-id="69257-102">The Sample Operations Error Handler</span></span>
<span data-ttu-id="69257-103">範例作業錯誤處理常式有三個主要組件： **OperationsClient**， **OperationsHandler**，和**OperationsServer**。</span><span class="sxs-lookup"><span data-stu-id="69257-103">The sample operations error handler has three major assemblies: **OperationsClient**, **OperationsHandler**, and **OperationsServer**.</span></span>  
  
 <span data-ttu-id="69257-104">這個解決方案會設定配接器使用**OpsClient**物件存放至**OperationsClient**組件。</span><span class="sxs-lookup"><span data-stu-id="69257-104">The solution configures the adapter to use the **OpsClient** object in the **OperationsClient** assembly.</span></span> <span data-ttu-id="69257-105">如您所預期， **OpsClient**物件會實作**IOpsAIC**介面。</span><span class="sxs-lookup"><span data-stu-id="69257-105">As you'd expect, the **OpsClient** object implements the **IOpsAIC** interface.</span></span>  
  
 <span data-ttu-id="69257-106">**OpsClient**物件會使用**IOperationsSystem**介面呼叫**OpsHandler**物件透過[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]遠端功能。</span><span class="sxs-lookup"><span data-stu-id="69257-106">The **OpsClient** object uses the **IOperationsSystem** interface to call the **OpsHandler** object through the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] remoting feature.</span></span> <span data-ttu-id="69257-107">**IOperationsSystem**介面顯示如下：</span><span class="sxs-lookup"><span data-stu-id="69257-107">The **IOperationsSystem** interface appears as follows:</span></span>  
  
```  
public interface IOperationsSystem  
{  
    void Initialize(string initData);  
    void Post(string originMachine, byte[] message);  
}  
  
```  
  
 <span data-ttu-id="69257-108">**OperationsServer**，主控台應用程式會接聽要求**OpsHandler**物件，並做為伺服器[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]遠端功能。</span><span class="sxs-lookup"><span data-stu-id="69257-108">The **OperationsServer**, a console application, listens for requests for the **OpsHandler** object and acts as the server for the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] remoting feature.</span></span> <span data-ttu-id="69257-109">呼叫**Execute**方法**OpsClient**物件接著會叫用**Post**方法**OpsHandler**物件。</span><span class="sxs-lookup"><span data-stu-id="69257-109">Calling the **Execute** method of the **OpsClient** object in turn invokes the **Post** method of the **OpsHandler** object.</span></span>  
  
 <span data-ttu-id="69257-110">**OpsHandler**方法的回應方式寫出其引數字串時，使用**追蹤**物件。</span><span class="sxs-lookup"><span data-stu-id="69257-110">The **OpsHandler** methods respond by writing out their argument strings using the **Trace** object.</span></span> <span data-ttu-id="69257-111">這會將錯誤公佈到主控台。</span><span class="sxs-lookup"><span data-stu-id="69257-111">This posts the errors to the console.</span></span> <span data-ttu-id="69257-112">如需有關**追蹤**物件，請參閱中的 「 追蹤類別 」[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]類別庫。</span><span class="sxs-lookup"><span data-stu-id="69257-112">For more information about the **Trace** object, see "Trace Class" in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Class Library.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69257-113">這裡的模式是在相同**OrderHandler**所在介面會指定用戶端與遠端物件之間的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="69257-113">The pattern here is the same as that in the **OrderHandler** in which an interface specifies the method calls between a client and a remoted object.</span></span> <span data-ttu-id="69257-114">不過，會產生額外一層之間的間接這裡**OpsClient**和**OpsHandler**。</span><span class="sxs-lookup"><span data-stu-id="69257-114">There is, however, an additional layer of indirection here between the **OpsClient** and the **OpsHandler**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69257-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69257-115">See Also</span></span>  
 [<span data-ttu-id="69257-116">Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="69257-116">The Ops Adapter</span></span>](../core/the-ops-adapter.md)
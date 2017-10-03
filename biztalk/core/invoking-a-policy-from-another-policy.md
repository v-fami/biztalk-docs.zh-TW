---
title: "叫用從另一個原則的原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5bf658a-02a1-426a-abe5-8c9de673cf0d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b03204b9de4b763f516b7fb22ada1f4f3f6173a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-a-policy-from-another-policy"></a><span data-ttu-id="db48d-102">從另一個原則叫用原則</span><span class="sxs-lookup"><span data-stu-id="db48d-102">Invoking a Policy from Another Policy</span></span>
<span data-ttu-id="db48d-103">您可以使用下列其中一種方法，從另一個原則 (父原則) 叫用原則 (子原則)：</span><span class="sxs-lookup"><span data-stu-id="db48d-103">You can invoke a policy (child) from another policy (parent) by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="db48d-104">呼叫**Policy.Execute**直接從父原則的方法</span><span class="sxs-lookup"><span data-stu-id="db48d-104">Calling the **Policy.Execute** method directly from the parent policy</span></span>  
  
-   <span data-ttu-id="db48d-105">呼叫的協助程式.NET 元件的方法包裝**Policy.Execute**方法從父原則</span><span class="sxs-lookup"><span data-stu-id="db48d-105">Calling a method of a helper .NET component that wraps the **Policy.Execute** method from the parent policy</span></span>  
  
 <span data-ttu-id="db48d-106">使用第二個方法的優點是，您可以加入前置處理和後置處理程式碼以**Policy.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-106">The advantage of using the second method is that you can add pre-processing and post-processing code to the **Policy.Execute** method.</span></span> <span data-ttu-id="db48d-107">例如，您可以在這個包裝函式方法中從子原則建立所需的任何事實。</span><span class="sxs-lookup"><span data-stu-id="db48d-107">For example, you can create any facts required from the child policy in this wrapper method.</span></span> <span data-ttu-id="db48d-108">下面幾節將提供每一個方法的範例。</span><span class="sxs-lookup"><span data-stu-id="db48d-108">The following sections provide an example for each method.</span></span>  
  
## <a name="invoking-the-policyexecute-method-directly-from-the-parent-policy"></a><span data-ttu-id="db48d-109">直接從父原則叫用 Policy.Execute 方法</span><span class="sxs-lookup"><span data-stu-id="db48d-109">Invoking the Policy.Execute Method Directly from the Parent Policy</span></span>  
 <span data-ttu-id="db48d-110">此章節提供使用叫用子原則，從父原則的高層級步驟**Policy.Execute**直接的方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-110">This section presents the high-level steps to invoke the child policy from the parent policy by using the **Policy.Execute** method directly.</span></span>  
  
### <a name="adding-the-policyexecute-action-to-the-parent-policy"></a><span data-ttu-id="db48d-111">將 Policy.Execute 動作加入到父原則</span><span class="sxs-lookup"><span data-stu-id="db48d-111">Adding the Policy.Execute Action to the Parent Policy</span></span>  
 <span data-ttu-id="db48d-112">下列程序中的步驟來新增**Policy.Execute**方法當做動作加入父原則會將 XML 文件當做事實傳遞給子原則。</span><span class="sxs-lookup"><span data-stu-id="db48d-112">The following procedure has steps to add the **Policy.Execute** method as an action to the parent policy that passes an XML document as a fact to the child policy.</span></span>  
  
##### <a name="to-add-the-policyexecute-method-as-an-action-to-a-policy"></a><span data-ttu-id="db48d-113">若要將 Policy.Execute 方法當做動作加入到原則</span><span class="sxs-lookup"><span data-stu-id="db48d-113">To add the Policy.Execute method as an action to a policy</span></span>  
  
1.  <span data-ttu-id="db48d-114">在 事實總管 視窗中，按一下**.NET 類別** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="db48d-114">In the Facts Explorer window, click the **.NET Classes** tab.</span></span>  
  
2.  <span data-ttu-id="db48d-115">以滑鼠右鍵按一下**.NET 組件**，然後按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="db48d-115">Right-click **.NET Assemblies**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="db48d-116">選取**Microsoft.RuleEngine**從**.NET 組件**清單，然後再按**確定**。</span><span class="sxs-lookup"><span data-stu-id="db48d-116">Select **Microsoft.RuleEngine** from the **.NET Assemblies** list, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="db48d-117">展開**原則**。</span><span class="sxs-lookup"><span data-stu-id="db48d-117">Expand **Policy**.</span></span>  
  
5.  <span data-ttu-id="db48d-118">拖曳**Execute (Object facts)**或**Execute （Object facts，IRuleSetTrackingInterceptor trackingInterceptor）**到 [THEN] 窗格。</span><span class="sxs-lookup"><span data-stu-id="db48d-118">Drag **Execute(Object facts)** or **Execute(Object facts, IRuleSetTrackingInterceptor trackingInterceptor)** to the THEN pane.</span></span>  
  
6.  <span data-ttu-id="db48d-119">按一下**XML 結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="db48d-119">Click the **XML Schemas** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db48d-120">在這個案例中，當做事實提交給父原則的 XML 文件會當做事實傳遞給子原則。</span><span class="sxs-lookup"><span data-stu-id="db48d-120">In this sample scenario, an XML document that is submitted as a fact to the parent policy is passed as a fact to the child policy.</span></span> <span data-ttu-id="db48d-121">您可以改為叫用會針對子原則建立事實的 .NET 方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-121">Instead, you can invoke a .NET method that creates the facts for the child policy.</span></span>  
  
7.  <span data-ttu-id="db48d-122">以滑鼠右鍵按一下**結構描述**，然後按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="db48d-122">Right-click **Schemas**, and then click **Browse**.</span></span>  
  
8.  <span data-ttu-id="db48d-123">選取您想要傳遞為事實，然後按一下 XML 文件的結構描述**開啟**。</span><span class="sxs-lookup"><span data-stu-id="db48d-123">Select the schema for the XML document you want to pass as a fact, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="db48d-124">拖曳*\<結構描述名稱 >*的第一個引數的.xsd **Policy.Execute**方法以傳遞給子原則的事實傳遞給父原則的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="db48d-124">Drag *\<Schema name>*.xsd to the first argument of the **Policy.Execute** method to pass the XML document that is passed to the parent policy as a fact to the child policy.</span></span>  
  
10. <span data-ttu-id="db48d-125">如果您使用**Execute**方法未採用**IRuleSetTrackingInterceptor**做為第二個引數，請略過下列步驟。</span><span class="sxs-lookup"><span data-stu-id="db48d-125">If you use the **Execute** method that does not take the **IRuleSetTrackingInterceptor** as the second argument, skip the following steps.</span></span>  
  
11. <span data-ttu-id="db48d-126">按一下**.NET 類別** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="db48d-126">Click the **.NET Classes** tab.</span></span>  
  
12. <span data-ttu-id="db48d-127">拖曳**DebugTrackingInterceptor**中**Microsoft.RuleEngine**的第二個引數**Policy.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-127">Drag **DebugTrackingInterceptor** in **Microsoft.RuleEngine** to the second argument of the **Policy.Execute** method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db48d-128">如果您執行此動作時，用戶端必須傳遞的執行個體**DebugTrackingInterceptor**類別作為事實到父原則中，依序將執行個體當做事實傳遞給子原則。</span><span class="sxs-lookup"><span data-stu-id="db48d-128">If you perform this action, the client must pass an instance of the **DebugTrackingInterceptor** class as a fact to the parent policy, which in turn passes the instance as a fact to the child policy.</span></span> <span data-ttu-id="db48d-129">相反地，您可以拖曳的建構函式**DebugTrackingInterceptor**類別，因此為您自動建立的執行個體。</span><span class="sxs-lookup"><span data-stu-id="db48d-129">Instead you could drag the constructor of the **DebugTrackingInterceptor** class so that the instance is automatically created for you.</span></span>  
  
### <a name="modifying-the-client-application-that-invokes-the-parent-policy"></a><span data-ttu-id="db48d-130">修改叫用父原則的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="db48d-130">Modifying the Client Application that Invokes the Parent Policy</span></span>  
 <span data-ttu-id="db48d-131">叫用父原則的用戶端建立的執行個體**原則**子原則名稱做為參數的類別並將它當做事實傳遞給父原則連同其他事實。</span><span class="sxs-lookup"><span data-stu-id="db48d-131">The client that invokes the parent policy creates an instance of the **Policy** class with the child policy name as a parameter and passes it as a fact to the parent policy along with other facts.</span></span> <span data-ttu-id="db48d-132">下列範例程式碼將說明這個動作：</span><span class="sxs-lookup"><span data-stu-id="db48d-132">The following sample code illustrates this action:</span></span>  
  
```  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
Policy policy = new Policy("ParentPolicy");  
object[] facts = new object[3];  
facts[0] = txd;  
facts[1] = new Policy("ChildPolicy");  
facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
 <span data-ttu-id="db48d-133">如果用戶端為 BizTalk 協調流程，您可能需要的程式碼放到建立事實**運算式**圖形，並將傳遞做為參數的 事實**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="db48d-133">If the client is a BizTalk orchestration, you may need to place the code to create facts in an **Expression** shape, and then pass the facts as parameters to the **Call Rules** shape.</span></span>  
  
## <a name="invoking-a-net-wrapper-method-from-the-parent-policy"></a><span data-ttu-id="db48d-134">從父原則叫用 .NET 包裝函式方法</span><span class="sxs-lookup"><span data-stu-id="db48d-134">Invoking a .NET Wrapper Method from the Parent Policy</span></span>  
 <span data-ttu-id="db48d-135">此章節提供要叫用的.NET 方法，以包裝對呼叫的概要步驟**Policy.Execute**從父原則的方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-135">This section presents the high-level steps to invoke a .NET method that wraps the call to the **Policy.Execute** method from the parent policy.</span></span>  
  
### <a name="creating-the-utility-net-class"></a><span data-ttu-id="db48d-136">建立公用程式 .NET 類別</span><span class="sxs-lookup"><span data-stu-id="db48d-136">Creating the Utility .NET Class</span></span>  
  
##### <a name="to-create-the-utility-class"></a><span data-ttu-id="db48d-137">若要建立公用程式類別</span><span class="sxs-lookup"><span data-stu-id="db48d-137">To create the utility class</span></span>  
  
1.  <span data-ttu-id="db48d-138">建立 .NET 類別庫專案，然後將類別加入此專案中。</span><span class="sxs-lookup"><span data-stu-id="db48d-138">Create a .NET class library project, and then add a class to the project.</span></span>  
  
2.  <span data-ttu-id="db48d-139">新增靜態方法，這個方法會呼叫**Policy.Execute**方法叫用原則，其名稱傳遞為參數，如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="db48d-139">Add a static method that calls the **Policy.Execute** method to invoke the policy whose name is passed as a parameter, as shown in the following sample code:</span></span>  
  
    ```  
    public static void Execute(string policyName, TypedXmlDocument txd)  
    {  
        DebugTrackingInterceptor dti = new   DebugTrackingInterceptor("PolicyTracking.txt");  
        Policy policy = new Policy("ParentPolicy");  
        object[] facts = new object[3];  
        facts[0] = txd;  
        facts[1] = new Policy("ChildPolicy");  
        facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
        policy.Execute(facts, dti);  
        policy.Dispose();  
    }   
    ```  
  
3.  <span data-ttu-id="db48d-140">請確定**StaticSupport**登錄機碼設為 1 或 2。</span><span class="sxs-lookup"><span data-stu-id="db48d-140">Make sure that the **StaticSupport** registry key is set to 1 or 2.</span></span> <span data-ttu-id="db48d-141">如需登錄機碼的詳細資訊，請參閱[叫用類別的靜態成員](../core/invoking-static-members-of-a-class.md)。</span><span class="sxs-lookup"><span data-stu-id="db48d-141">For more information about the registry key, see [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db48d-142">您可以使用執行個體方法，而不是靜態方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-142">You can use an instance method instead of a static method.</span></span> <span data-ttu-id="db48d-143">請記得，如果您使用執行個體方法，用戶端必須將協助程式 .NET 類別的執行個體當做事實傳遞給父原則。</span><span class="sxs-lookup"><span data-stu-id="db48d-143">Remember that, if you use an instance method, the client must pass an instance of the helper .NET class as a fact to the parent policy.</span></span>  
  
### <a name="modifying-the-client-application"></a><span data-ttu-id="db48d-144">修改用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="db48d-144">Modifying the Client Application</span></span>  
 <span data-ttu-id="db48d-145">用戶端叫用父原則，然後父原則叫用會叫用子原則的協助程式方法。</span><span class="sxs-lookup"><span data-stu-id="db48d-145">The client invokes the parent policy, and the parent policy invokes the helper method that invokes the child policy.</span></span> <span data-ttu-id="db48d-146">用戶端的範例程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="db48d-146">The sample code for the client is as follows:</span></span>  
  
```  
facts[0] = txd;  
facts[1] = new PolicyExecutor(txd);  
//call the first or parent policy  
Policy policy = new Policy(policyName);  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
> [!NOTE]
>  <span data-ttu-id="db48d-147">如果此方法為執行個體方法，用戶端必須建立協助程式 .NET 類別的執行個體，並將它當做事實傳遞給父原則。</span><span class="sxs-lookup"><span data-stu-id="db48d-147">If the method is an instance method, the client must create an instance of the helper .NET class, and pass it as a fact to the parent policy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db48d-148">如果用戶端為 BizTalk 協調流程，您可能需要的程式碼放到建立事實**運算式**圖形，並將傳遞做為參數的 事實**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="db48d-148">If the client is a BizTalk orchestration, you may need to place the code to create facts in an **Expression** shape, and then pass the facts as parameters to the **Call Rules** shape.</span></span>
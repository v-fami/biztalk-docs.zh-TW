---
title: 叫用 SAP 使用 WCF 服務模型中的 Bapi |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAPIs, invoking by using the WCF service model
- WCF service model, invoking BAPIs
ms.assetid: be3c48d6-2213-4ae5-97f4-634fbc423022
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 437c88516cfb771e0e5ae10807391235d602eb37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218510"
---
# <a name="invoke-bapis-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="64159-102">叫用 SAP 使用 WCF 服務模型中的 Bapi</span><span class="sxs-lookup"><span data-stu-id="64159-102">Invoke BAPIs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="64159-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現為 Bapi:</span><span class="sxs-lookup"><span data-stu-id="64159-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs as:</span></span>  
  
-   <span data-ttu-id="64159-104">**RFC 作業**。</span><span class="sxs-lookup"><span data-stu-id="64159-104">**RFC operations**.</span></span> <span data-ttu-id="64159-105">中的 RFC 節點下便會顯示像是其他任何 RFC Bapi [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="64159-105">BAPIs like any other RFC are surfaced under the RFC node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="64159-106">**SAP 商務物件方法**。</span><span class="sxs-lookup"><span data-stu-id="64159-106">**Methods of SAP business objects**.</span></span> <span data-ttu-id="64159-107">當做商務物件的方法，Bapi 由商務物件中的 BAPI 節點下顯示[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="64159-107">As methods of business objects, BAPIs are surfaced by business object under the BAPI node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
 <span data-ttu-id="64159-108">叫用 BAPI RFC 作業或商務物件方法時，是否每個 BAPI 一定是 LUW SAP 系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="64159-108">Whether you invoke a BAPI as an RFC operation or as a business object method, each BAPI is always part of an LUW on the SAP system.</span></span>  
  
 <span data-ttu-id="64159-109">如需如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 Bapi，請參閱[SAP 中的 Bapi 作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="64159-109">For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports BAPIs, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
 <span data-ttu-id="64159-110">當您叫用商務物件方法為 Bapi 使用 WCF 服務模型時，每個 SAP 商務物件由 WCF 用戶端類別，而且該商務物件的 Bapi 都會以做為用戶端上的方法。</span><span class="sxs-lookup"><span data-stu-id="64159-110">When you use the WCF service model to invoke BAPIs as business object methods, each SAP business object is represented by a WCF client class and the BAPIs of that business object are represented as methods on the client.</span></span> <span data-ttu-id="64159-111">您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別的特定商務物件，其中包含方法的每個您想要叫用程式碼中的 BAPI。</span><span class="sxs-lookup"><span data-stu-id="64159-111">You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class for specific business objects that contains methods for each BAPI that you want to invoke in your code.</span></span> <span data-ttu-id="64159-112">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生封裝的參數和資料類型所使用的每個 BAPI 的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="64159-112">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates .NET types to encapsulate the parameters and data types that are used by each BAPI.</span></span> <span data-ttu-id="64159-113">然後，您可以建立此 WCF 用戶端類別的執行個體，並呼叫其方法來叫用目標 Bapi。</span><span class="sxs-lookup"><span data-stu-id="64159-113">You can then create an instance of this WCF client class and call its methods to invoke the target BAPIs.</span></span>  
  
 <span data-ttu-id="64159-114">下列各節將說明如何以商務物件的方法叫用的 Bapi 和討論如何在 WCF 服務模型中支援 BAPI 的交易。</span><span class="sxs-lookup"><span data-stu-id="64159-114">The following sections show you how to invoke BAPIs as methods of business objects and discuss how BAPI transactions are supported in the WCF service model.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="64159-115">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="64159-115">The WCF Client Class</span></span>  
 <span data-ttu-id="64159-116">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現不同的服務合約，每個商務物件。</span><span class="sxs-lookup"><span data-stu-id="64159-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a different service contract, for each business object.</span></span> <span data-ttu-id="64159-117">這表示，每個商務物件的唯一 WCF 建立用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="64159-117">This means that for each business object a unique WCF client class is created.</span></span> <span data-ttu-id="64159-118">這個類別的名稱根據商務物件型別。</span><span class="sxs-lookup"><span data-stu-id="64159-118">The name of this class is based on the business object type.</span></span> <span data-ttu-id="64159-119">例如銷售訂單商務物件 （商務物件類型 BUS2032） 中，WCF 用戶端類別是**BapiBUS2032Client**。</span><span class="sxs-lookup"><span data-stu-id="64159-119">For example for the Sales Order business object (business object type BUS2032), the WCF client class is **BapiBUS2032Client**.</span></span> <span data-ttu-id="64159-120">每個目標 BAPI 中的商務物件被以產生 WCF 用戶端類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="64159-120">Each target BAPI in the business object is represented as a method in the generated WCF client class.</span></span> <span data-ttu-id="64159-121">在每個方法：</span><span class="sxs-lookup"><span data-stu-id="64159-121">In each method:</span></span>  
  
-   <span data-ttu-id="64159-122">SAP 匯出參數當成**出**參數</span><span class="sxs-lookup"><span data-stu-id="64159-122">SAP export parameters are surfaced as **out** parameters</span></span>  
  
-   <span data-ttu-id="64159-123">SAP 呼叫參數當成**ref**參數。</span><span class="sxs-lookup"><span data-stu-id="64159-123">SAP calling parameters are surfaced as **ref** parameters.</span></span>  
  
-   <span data-ttu-id="64159-124">複雜的 SAP 類型，例如結構顯示為.NET 類別有屬性對應至 SAP 類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="64159-124">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="64159-125">這些類別會定義下列命名空間中： microsoft.lobservices.sap._2007._03.Types.Rfc。</span><span class="sxs-lookup"><span data-stu-id="64159-125">These classes are defined in the following namespace: microsoft.lobservices.sap._2007._03.Types.Rfc.</span></span>  
  
 <span data-ttu-id="64159-126">BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 便會顯示每個商務物件，您應該永遠包含在您的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="64159-126">BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK are surfaced for each business object and you should always include these in your WCF client.</span></span>  
  
 <span data-ttu-id="64159-127">下列程式碼顯示針對 銷售訂單的商務物件產生 WCF 用戶端類別的一部分。</span><span class="sxs-lookup"><span data-stu-id="64159-127">The following code shows part of a WCF client class generated for the Sales Order business object.</span></span> <span data-ttu-id="64159-128">此用戶端包含 CREATEFROMDAT2、 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="64159-128">This client contains methods to invoke CREATEFROMDAT2, BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK.</span></span> <span data-ttu-id="64159-129">為了清楚起見，建構函式和其他程式碼已省略。</span><span class="sxs-lookup"><span data-stu-id="64159-129">For clarity the constructors and other code has been omitted.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class BapiBUS2032Client : System.ServiceModel.ClientBase<BapiBUS2032>, BapiBUS2032 {  
  
    // Code has been removed for clarity  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="SALESDOCUMENT">Number of Generated Document</param>  
    /// <param name="BEHAVE_WHEN_ERROR">Error Handling</param>  
    /// …  
    /// <param name="ORDER_TEXT">Texts</param>  
    /// <param name="PARTNERADDRESSES">BAPI Reference Structure for Addresses (Org./Company)</param>  
    /// <param name="RETURN">Return Messages</param>  
    /// <returns></returns>  
    public string CREATEFROMDAT2(  
                string BEHAVE_WHEN_ERROR,   
                string BINARY_RELATIONSHIPTYPE,   
                string CONVERT,   
                string INT_NUMBER_ASSIGNMENT,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDLS LOGIC_SWITCH,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1 ORDER_HEADER_IN,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDHD1X ORDER_HEADER_INX,   
                string SALESDOCUMENTIN,   
                microsoft.lobservices.sap._2007._03.Types.Rfc.BAPI_SENDER SENDER,   
                string TESTRUN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPAREX[] EXTENSIONIN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICCARD[] ORDER_CCARD,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUBLB[] ORDER_CFGS_BLOB,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUINS[] ORDER_CFGS_INST,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUPRT[] ORDER_CFGS_PART_OF,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUCFG[] ORDER_CFGS_REF,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUREF[] ORDER_CFGS_REFINST,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUVAL[] ORDER_CFGS_VALUE,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICUVK[] ORDER_CFGS_VK,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICOND[] ORDER_CONDITIONS_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPICONDX[] ORDER_CONDITIONS_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDITM[] ORDER_ITEMS_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDITMX[] ORDER_ITEMS_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDKEY[] ORDER_KEYS,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIPARNR[] ORDER_PARTNERS,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISCHDL[] ORDER_SCHEDULES_IN,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISCHDLX[] ORDER_SCHEDULES_INX,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPISDTEXT[] ORDER_TEXT,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIADDR1[] PARTNERADDRESSES,   
                ref microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2[] RETURN) { ...}  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="RETURN">Confirmations</param>  
    /// <param name="WAIT">Using the command `COMMIT AND WAIT`</param>  
    /// <returns></returns>  
    public microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2 BAPI_TRANSACTION_COMMIT(string WAIT) { ... }  
  
    /// <summary>The Metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="RETURN">Confirmations</param>  
    /// <returns></returns>  
    public microsoft.lobservices.sap._2007._03.Types.Rfc.BAPIRET2 BAPI_TRANSACTION_ROLLBACK() { ... }  
}  
```  
  
## <a name="bapi-transactions-in-the-wcf-service-model"></a><span data-ttu-id="64159-130">WCF 服務模型中的 BAPI 交易</span><span class="sxs-lookup"><span data-stu-id="64159-130">BAPI Transactions in the WCF Service Model</span></span>  
 <span data-ttu-id="64159-131">每個 BAPI，是否為 RFC 或商務物件方法會叫用是交易的一部分 (LUW) SAP 系統。而透過相同的 SAP 連線收到每個 BAPI 是 SAP 系統的相同 BAPI 交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="64159-131">Every BAPI, whether it is invoked as an RFC or as a business object method, is part of a transaction (LUW) on the SAP system; and every BAPI received over the same SAP connection is part of the same BAPI transaction on the SAP system.</span></span> <span data-ttu-id="64159-132">SAP 認可或回復 BAPI 交易，當它收到 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 連接上。</span><span class="sxs-lookup"><span data-stu-id="64159-132">SAP commits or rolls back the BAPI transaction when it receives a BAPI_TRANSACTION_COMMIT or a BAPI_TRANSACTION_ROLLBACK on the connection.</span></span> <span data-ttu-id="64159-133">執行 commit 或 rollback 之後，透過連接接收下一個 BAPI 開始新交易。</span><span class="sxs-lookup"><span data-stu-id="64159-133">After a commit or rollback has been performed, the next BAPI received over the connection begins a new transaction.</span></span>  
  
 <span data-ttu-id="64159-134">配接器的每個 WCF 通道會有專用的 SAP 連接。</span><span class="sxs-lookup"><span data-stu-id="64159-134">For the adapter each WCF channel has a dedicated SAP connection.</span></span> <span data-ttu-id="64159-135">在 WCF 服務模型中，每個 WCF 用戶端具有使用的傳送郵件給 SAP 系統的內部通道。</span><span class="sxs-lookup"><span data-stu-id="64159-135">In the WCF service model, each WCF client has an inner channel that is used send messages to the SAP system.</span></span> <span data-ttu-id="64159-136">這表示使用特定 WCF 用戶端叫用的 Bapi 為 SAP 系統上唯一的 BAPI 交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="64159-136">This means that the BAPIs that are invoked using a specific WCF client are part of a unique BAPI transaction on the SAP system.</span></span> <span data-ttu-id="64159-137">這會是重要的限制，當您使用 WCF 服務模型來叫用商務物件方法的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="64159-137">This imposes a significant limitation when you use the WCF service model to invoke BAPIs as business object methods.</span></span> <span data-ttu-id="64159-138">因為每個 SAP 商務物件由專用的 WCF 用戶端類別，您無法從叫用 Bapi 兩個不同的商務物件相同交易的一部份。</span><span class="sxs-lookup"><span data-stu-id="64159-138">Because each SAP business object is represented by a dedicated WCF client class, you cannot invoke BAPIs from two different business objects as part of the same transaction.</span></span> <span data-ttu-id="64159-139">解決這個問題的方式是叫用做為 RFC 作業 Bapi。</span><span class="sxs-lookup"><span data-stu-id="64159-139">The way around this is to invoke the BAPIs as RFC operations.</span></span> <span data-ttu-id="64159-140">這是因為[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 RFC 作業的單一 WCF 用戶端，因此，透過相同的 WCF 通道傳送所有使用該用戶端叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="64159-140">This is because the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates a single WCF client for RFC operations, and, therefore, all operations invoked using that client are sent over the same WCF channel.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64159-141">如果您想要從相同的 BAPI 交易中的不同 SAP 商務物件包含 Bapi，您必須為 RFC 作業 （使用相同的 WCF 用戶端） 叫用它們。</span><span class="sxs-lookup"><span data-stu-id="64159-141">If you want to include BAPIs from different SAP business objects in the same BAPI transaction, you must invoke them as RFC operations (using the same WCF client).</span></span> <span data-ttu-id="64159-142">您無法當做商務物件方法來叫用這些設定。</span><span class="sxs-lookup"><span data-stu-id="64159-142">You cannot invoke them as business object methods.</span></span>  
  
 <span data-ttu-id="64159-143">您可以呼叫 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 認可或復原 BAPI 交易上的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="64159-143">You call BAPI_TRANSACTION_COMMIT or BAPI_TRANSACTION_ROLLBACK to commit or roll back the BAPI transaction on the SAP system.</span></span> <span data-ttu-id="64159-144">配接器會提供諸如這些兩個 Bapi:</span><span class="sxs-lookup"><span data-stu-id="64159-144">The adapter surfaces these two BAPIs:</span></span>  
  
-   <span data-ttu-id="64159-145">在做為 RFC 作業的基礎節點。</span><span class="sxs-lookup"><span data-stu-id="64159-145">Under the Basis node as RFC operations.</span></span>  
  
-   <span data-ttu-id="64159-146">在每個商務物件。</span><span class="sxs-lookup"><span data-stu-id="64159-146">Under each business object.</span></span>  
  
 <span data-ttu-id="64159-147">如需配接器上 SAP 所支援的 BAPI 交易的詳細資訊，請參閱[SAP 中的 Bapi 作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="64159-147">For more information about how the adapter supports BAPI transactions on SAP, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
## <a name="how-to-create-an-application-that-invokes-bapis-as-methods-of-business-objects"></a><span data-ttu-id="64159-148">如何建立以商務物件的方法叫用的 Bapi 的應用程式</span><span class="sxs-lookup"><span data-stu-id="64159-148">How to Create an Application that Invokes BAPIs as Methods of Business Objects</span></span>  
 <span data-ttu-id="64159-149">本節提供如何以商務物件的方法叫用的 Bapi 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="64159-149">This section provides information about how to invoke BAPIs as methods of business objects.</span></span> <span data-ttu-id="64159-150">做為 RFC 作業叫用的 Bapi，不同之處在於您建立目標為 RFC 作業 Bapi 的 WCF 用戶端，並用來叫用每個 BAPI 應該遵循相同的基本程序。</span><span class="sxs-lookup"><span data-stu-id="64159-150">The same basic procedure should be followed to invoke BAPIs as RFC operations, except that you create a WCF client that targets the BAPIs as RFC operations and use it to invoke each BAPI.</span></span>  
  
 <span data-ttu-id="64159-151">若要建立 BAPI 的用戶端應用程式，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="64159-151">To create a BAPI client application, perform the following steps.</span></span>  
  
#### <a name="to-create-an-bapi-client-application"></a><span data-ttu-id="64159-152">若要建立的 BAPI 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="64159-152">To create an BAPI client application</span></span>  
  
1.  <span data-ttu-id="64159-153">產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="64159-153">Generate a WCF client class.</span></span> <span data-ttu-id="64159-154">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別 （或類別） 為目標的商務物件和您想要的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="64159-154">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class (or classes) that targets the business objects and BAPIs with which you want to work.</span></span> <span data-ttu-id="64159-155">請務必包含 BAPI_TRANSACTION_COMMIT BAPI_TRANSACTION_ROLLBACK 公開和方法 (Bapi) 的每個目標商務物件。</span><span class="sxs-lookup"><span data-stu-id="64159-155">Be sure to include the BAPI_TRANSACTION_COMMIT and the BAPI_TRANSACTION_ROLLBACK methods (BAPIs) exposed for each target business object.</span></span> <span data-ttu-id="64159-156">如需如何產生 WCF 用戶端的詳細資訊，請參閱[SAP 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="64159-156">For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2.  <span data-ttu-id="64159-157">建立在步驟 1 所產生的 WCF 用戶端類別的執行個體並建立及設定 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="64159-157">Create an instance of the WCF client class generated in step 1, and create and configure a WCF client.</span></span> <span data-ttu-id="64159-158">設定 WCF 用戶端包含指定繫結與用戶端會使用的端點位址。</span><span class="sxs-lookup"><span data-stu-id="64159-158">Configuring the WCF client involves specifying the binding and endpoint address that the client will use.</span></span> <span data-ttu-id="64159-159">您可以在程式碼中以命令方式或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="64159-159">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="64159-160">如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="64159-160">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="64159-161">下列程式碼初始化銷售訂單 (BUS2032) SAP 商務物件，從設定的 WCF 用戶端，以及設定 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="64159-161">The following code initializes the WCF client for the Sales Order (BUS2032) SAP business object from configuration and sets the credentials for the SAP system.</span></span>  
  
    ```  
    BapiBUS2032Client bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
    bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
    bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  <span data-ttu-id="64159-162">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="64159-162">Open the WCF client.</span></span>  
  
    ```  
    bapiClient.Open();  
    ```  
  
4.  <span data-ttu-id="64159-163">叫用 WCF 用戶端上步驟 2 中建立適當的 Bapi SAP 系統上叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="64159-163">Invoke methods on the WCF client created in step 2 to invoke the appropriate BAPIs on the SAP system.</span></span> <span data-ttu-id="64159-164">您可以叫用多個 SAP 系統上的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="64159-164">You can invoke multiple BAPIs on the SAP system.</span></span>  
  
5.  <span data-ttu-id="64159-165">結束的交易：</span><span class="sxs-lookup"><span data-stu-id="64159-165">End the transaction by:</span></span>  
  
    1.  <span data-ttu-id="64159-166">叫用 BAPI_TRANSACTION_COMMIT 方法認可交易。</span><span class="sxs-lookup"><span data-stu-id="64159-166">Invoking the BAPI_TRANSACTION_COMMIT method to commit the transaction.</span></span>  
  
        ```  
        bapiClient.BAPI_TRANSACTION_COMMIT("X");  
        ```  
  
    2.  <span data-ttu-id="64159-167">叫用 BAPI_TRANSACTION_ROLLBACK 方法來回復交易。</span><span class="sxs-lookup"><span data-stu-id="64159-167">Invoking the BAPI_TRANSACTION_ROLLBACK method to roll back the transaction.</span></span>  
  
        ```  
        bapiClient.BAPI_TRANSACTION_ROLLBACK();  
        ```  
  
6.  <span data-ttu-id="64159-168">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="64159-168">Close the WCF client.</span></span>  
  
    ```  
    bapiClient.Close();   
    ```  
  
### <a name="example"></a><span data-ttu-id="64159-169">範例</span><span class="sxs-lookup"><span data-stu-id="64159-169">Example</span></span>  
 <span data-ttu-id="64159-170">下列範例會叫用 CREATEFROMDAT2 BAPI 的銷售訂單的商務物件。</span><span class="sxs-lookup"><span data-stu-id="64159-170">The following example invokes the CREATEFROMDAT2 BAPI on the Sales Order business object.</span></span> <span data-ttu-id="64159-171">它會叫用的 BAPI 數次，然後再叫用 BAPI_TRANSACTION_COMMIT 認可交易。</span><span class="sxs-lookup"><span data-stu-id="64159-171">It invokes the BAPI several times and then invokes BAPI_TRANSACTION_COMMIT to commit the transaction.</span></span> <span data-ttu-id="64159-172">如果發生錯誤時叫用 BAPI，BAPI_TRANSACTION_ROLLBACK 會叫用來回復交易的例外狀況處理常式中。</span><span class="sxs-lookup"><span data-stu-id="64159-172">If an error occurs when invoking the BAPI, BAPI_TRANSACTION_ROLLBACK is invoked in the exception handler to roll back the transaction.</span></span>  
  
 <span data-ttu-id="64159-173">CREATEFROMDAT2 方法會採用許多參數。這些會在範例中，為了簡短起見省略。</span><span class="sxs-lookup"><span data-stu-id="64159-173">The CREATEFROMDAT2 method takes many parameters; these are omitted in the example for the sake of brevity.</span></span> <span data-ttu-id="64159-174">您可以找到範例，示範 Microsoft 所隨附的範例中的 BAPI 交易[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="64159-174">You can find a sample that demonstrates BAPI transactions in the samples shipped with the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="64159-175">如需詳細資訊，請參閱[適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="64159-175">For more information, see [Samples for the SAP Adapter ](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
using microsoft.lobservices.sap._2007._03.Types.Rfc;  
  
// This Example demonstrates BAPI transactions. Two sales orders are  
// created using the CREATEFROMDAT2 method of a SAP Business Object.   
// After the orders are created, the BAPI transaction is committed.   
// If an exception occurs when sending the BAPIs, the BAPI transaction is   
// rolled back.  
//   
  
namespace SapBapiTxClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the BAPI client from the generated endpoint configuration.  
  
            BapiBUS2032Client bapiClient = null;  
  
            Console.WriteLine("BAPI transaction sample started");  
            Console.WriteLine("\nCreating business object client");  
  
            try  
            {  
                bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
                bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
                bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the BAPI Client  
                bapiClient.Open();  
  
                ...  
  
                // send first BAPI  
                try  
                {  
                    string salesDocNumber1 = bapiClient.CREATEFROMDAT2(  
                        ...  
                        // parameters ommitted  
                        ...                          
                        );  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
                // send second BAPI  
                try  
                {  
                    string salesDocNumber1 = bapiClient.CREATEFROMDAT2(  
                        ...  
                        // parameters omitted  
                        ...                          
                        );  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
                // Commit BAPI Transaction  
                try  
                {  
                    bapiClient.BAPI_TRANSACTION.Commit();  
                }  
                catch (Exception ex)  
                {  
                    bapiClient.BAPI_TRANSACTION_ROLLBACK();  
                    throw;  
                }  
  
                ...  
  
            }  
            catch (ConnectionException cex)  
            {  
                // Get here if problem connecting to the SAP system   
  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                // Get here if the SAP system returns an exception  
  
                Console.WriteLine("Exception occurred on the SAP System");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
            // Close the client when finished  
                if (bapiClient != null)  
                {  
                    if (bapiClient.State == CommunicationState.Opened)  
                        bapiClient.Close();  
                    else  
                        bapiClient.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="64159-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64159-176">See Also</span></span>  
[<span data-ttu-id="64159-177">開發應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="64159-177">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)  
 [<span data-ttu-id="64159-178">SAP 中的 Bapi 的作業</span><span class="sxs-lookup"><span data-stu-id="64159-178">Operations on BAPIs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)
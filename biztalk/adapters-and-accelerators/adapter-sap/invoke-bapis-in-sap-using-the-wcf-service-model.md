---
title: 叫用 SAP 使用 WCF 服務模型中的 Bapi |Microsoft Docs
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
ms.openlocfilehash: b6f5cab88b0f672f9f09bdeb7795c0a58213f92f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002439"
---
# <a name="invoke-bapis-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="ed88e-102">叫用 SAP 使用 WCF 服務模型中的 Bapi</span><span class="sxs-lookup"><span data-stu-id="ed88e-102">Invoke BAPIs in SAP using the WCF Service Model</span></span>
<span data-ttu-id="ed88e-103">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]瀏覽 Bapi 為：</span><span class="sxs-lookup"><span data-stu-id="ed88e-103">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs as:</span></span>  
  
- <span data-ttu-id="ed88e-104">**RFC 作業**。</span><span class="sxs-lookup"><span data-stu-id="ed88e-104">**RFC operations**.</span></span> <span data-ttu-id="ed88e-105">在 RFC 節點下顯示 Bapi 像任何其他的 RFC [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed88e-105">BAPIs like any other RFC are surfaced under the RFC node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
- <span data-ttu-id="ed88e-106">**SAP 商務物件方法**。</span><span class="sxs-lookup"><span data-stu-id="ed88e-106">**Methods of SAP business objects**.</span></span> <span data-ttu-id="ed88e-107">作為商務物件的方法，商務物件中的 BAPI 節點下顯示 Bapi [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed88e-107">As methods of business objects, BAPIs are surfaced by business object under the BAPI node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
  <span data-ttu-id="ed88e-108">您叫用 BAPI 以 RFC 作業或商務物件方法時，是否每個 BAPI 一定是 LUW 上 SAP 系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed88e-108">Whether you invoke a BAPI as an RFC operation or as a business object method, each BAPI is always part of an LUW on the SAP system.</span></span>  
  
  <span data-ttu-id="ed88e-109">如需如何[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援 Bapi，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="ed88e-109">For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports BAPIs, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
  <span data-ttu-id="ed88e-110">當您叫用 Bapi 商務物件方法為使用 WCF 服務模型時，每個 SAP 商務物件由 WCF 用戶端類別，而且該商務物件的 Bapi 都會表示為用戶端上的方法。</span><span class="sxs-lookup"><span data-stu-id="ed88e-110">When you use the WCF service model to invoke BAPIs as business object methods, each SAP business object is represented by a WCF client class and the BAPIs of that business object are represented as methods on the client.</span></span> <span data-ttu-id="ed88e-111">您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別特定的商務物件，包含適用於每個您想要叫用程式碼中的 BAPI 方法。</span><span class="sxs-lookup"><span data-stu-id="ed88e-111">You can use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class for specific business objects that contains methods for each BAPI that you want to invoke in your code.</span></span> <span data-ttu-id="ed88e-112">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生封裝的參數和資料類型所使用的每個 BAPI 的.NET 型別。</span><span class="sxs-lookup"><span data-stu-id="ed88e-112">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates .NET types to encapsulate the parameters and data types that are used by each BAPI.</span></span> <span data-ttu-id="ed88e-113">接著，您可以建立此 WCF 用戶端類別的執行個體，並呼叫其方法來叫用 Bapi 的目標。</span><span class="sxs-lookup"><span data-stu-id="ed88e-113">You can then create an instance of this WCF client class and call its methods to invoke the target BAPIs.</span></span>  
  
  <span data-ttu-id="ed88e-114">下列各節會示範如何以商務物件的方法叫用 Bapi 及討論如何在 WCF 服務模型中支援 BAPI 交易。</span><span class="sxs-lookup"><span data-stu-id="ed88e-114">The following sections show you how to invoke BAPIs as methods of business objects and discuss how BAPI transactions are supported in the WCF service model.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="ed88e-115">WCF 用戶端類別</span><span class="sxs-lookup"><span data-stu-id="ed88e-115">The WCF Client Class</span></span>  
 <span data-ttu-id="ed88e-116">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現不同的服務合約，為每個商務物件。</span><span class="sxs-lookup"><span data-stu-id="ed88e-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces a different service contract, for each business object.</span></span> <span data-ttu-id="ed88e-117">這表示，每個商務物件的唯一 WCF 建立用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="ed88e-117">This means that for each business object a unique WCF client class is created.</span></span> <span data-ttu-id="ed88e-118">這個類別的名稱根據商務物件型別。</span><span class="sxs-lookup"><span data-stu-id="ed88e-118">The name of this class is based on the business object type.</span></span> <span data-ttu-id="ed88e-119">例如針對銷售訂單商務物件 （商務物件類型 BUS2032） 中，WCF 用戶端類別是**BapiBUS2032Client**。</span><span class="sxs-lookup"><span data-stu-id="ed88e-119">For example for the Sales Order business object (business object type BUS2032), the WCF client class is **BapiBUS2032Client**.</span></span> <span data-ttu-id="ed88e-120">在商務物件中每個目標 BAPI 被以產生 WCF 用戶端類別中的方法。</span><span class="sxs-lookup"><span data-stu-id="ed88e-120">Each target BAPI in the business object is represented as a method in the generated WCF client class.</span></span> <span data-ttu-id="ed88e-121">在每個方法：</span><span class="sxs-lookup"><span data-stu-id="ed88e-121">In each method:</span></span>  
  
- <span data-ttu-id="ed88e-122">SAP 匯出參數當成**出**參數</span><span class="sxs-lookup"><span data-stu-id="ed88e-122">SAP export parameters are surfaced as **out** parameters</span></span>  
  
- <span data-ttu-id="ed88e-123">SAP 呼叫參數當成**ref**參數。</span><span class="sxs-lookup"><span data-stu-id="ed88e-123">SAP calling parameters are surfaced as **ref** parameters.</span></span>  
  
- <span data-ttu-id="ed88e-124">複雜的 SAP 類型，例如結構顯示為.NET 類別，其屬性會對應到 SAP 類型的欄位。</span><span class="sxs-lookup"><span data-stu-id="ed88e-124">Complex SAP types such as structures are surfaced as .NET classes with properties that correspond to the fields of the SAP type.</span></span> <span data-ttu-id="ed88e-125">這些類別定義在下列命名空間： microsoft.lobservices.sap._2007._03.Types.Rfc。</span><span class="sxs-lookup"><span data-stu-id="ed88e-125">These classes are defined in the following namespace: microsoft.lobservices.sap._2007._03.Types.Rfc.</span></span>  
  
  <span data-ttu-id="ed88e-126">BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 會呈現每個商務物件，您應該一律包含在您的 WCF 用戶端中。</span><span class="sxs-lookup"><span data-stu-id="ed88e-126">BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK are surfaced for each business object and you should always include these in your WCF client.</span></span>  
  
  <span data-ttu-id="ed88e-127">下列程式碼顯示針對銷售訂單的商務物件產生 WCF 用戶端類別的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed88e-127">The following code shows part of a WCF client class generated for the Sales Order business object.</span></span> <span data-ttu-id="ed88e-128">此用戶端包含 CREATEFROMDAT2、 BAPI_TRANSACTION_COMMIT 和 BAPI_TRANSACTION_ROLLBACK 叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="ed88e-128">This client contains methods to invoke CREATEFROMDAT2, BAPI_TRANSACTION_COMMIT and BAPI_TRANSACTION_ROLLBACK.</span></span> <span data-ttu-id="ed88e-129">為了清楚起見已省略建構函式和其他程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed88e-129">For clarity the constructors and other code has been omitted.</span></span>  
  
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
  
## <a name="bapi-transactions-in-the-wcf-service-model"></a><span data-ttu-id="ed88e-130">WCF 服務模型中的 BAPI 交易</span><span class="sxs-lookup"><span data-stu-id="ed88e-130">BAPI Transactions in the WCF Service Model</span></span>  
 <span data-ttu-id="ed88e-131">每個 BAPI 中，是否會叫用 RFC 或商務物件方法，是交易的一部分 (LUW) 上的 SAP 系統;並透過相同的 SAP 連線收到每個 BAPI 是 SAP 系統上相同的 BAPI 交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed88e-131">Every BAPI, whether it is invoked as an RFC or as a business object method, is part of a transaction (LUW) on the SAP system; and every BAPI received over the same SAP connection is part of the same BAPI transaction on the SAP system.</span></span> <span data-ttu-id="ed88e-132">SAP 會認可或回復 BAPI 交易，當它收到 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 連接上。</span><span class="sxs-lookup"><span data-stu-id="ed88e-132">SAP commits or rolls back the BAPI transaction when it receives a BAPI_TRANSACTION_COMMIT or a BAPI_TRANSACTION_ROLLBACK on the connection.</span></span> <span data-ttu-id="ed88e-133">執行 commit 或 rollback 之後下, 一步 的 BAPI 透過連接接收就會開始新交易。</span><span class="sxs-lookup"><span data-stu-id="ed88e-133">After a commit or rollback has been performed, the next BAPI received over the connection begins a new transaction.</span></span>  
  
 <span data-ttu-id="ed88e-134">配接器的每個 WCF 通道會有專用的 SAP 連接。</span><span class="sxs-lookup"><span data-stu-id="ed88e-134">For the adapter each WCF channel has a dedicated SAP connection.</span></span> <span data-ttu-id="ed88e-135">在 WCF 服務模型中，每個 WCF 用戶端會有已使用的傳送訊息到 SAP 系統的內部通道。</span><span class="sxs-lookup"><span data-stu-id="ed88e-135">In the WCF service model, each WCF client has an inner channel that is used send messages to the SAP system.</span></span> <span data-ttu-id="ed88e-136">這表示使用特定的 WCF 用戶端會叫用 Bapi 是唯一的 BAPI 交易上的 SAP 系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed88e-136">This means that the BAPIs that are invoked using a specific WCF client are part of a unique BAPI transaction on the SAP system.</span></span> <span data-ttu-id="ed88e-137">當叫用 Bapi 當做商務物件方法的情況下，您在使用 WCF 服務模型時，這會是重要的限制。</span><span class="sxs-lookup"><span data-stu-id="ed88e-137">This imposes a significant limitation when you use the WCF service model to invoke BAPIs as business object methods.</span></span> <span data-ttu-id="ed88e-138">因為每個 SAP 商務物件由專用的 WCF 用戶端類別，您無法從叫用 Bapi 兩個不同的商務物件為相同交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="ed88e-138">Because each SAP business object is represented by a dedicated WCF client class, you cannot invoke BAPIs from two different business objects as part of the same transaction.</span></span> <span data-ttu-id="ed88e-139">解決這個問題的方式是叫用 RFC 作業的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="ed88e-139">The way around this is to invoke the BAPIs as RFC operations.</span></span> <span data-ttu-id="ed88e-140">這是因為[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]會產生單一 RFC 作業的 WCF 用戶端，因此，透過相同的 WCF 通道傳送所有使用該用戶端叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="ed88e-140">This is because the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates a single WCF client for RFC operations, and, therefore, all operations invoked using that client are sent over the same WCF channel.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed88e-141">如果您想要包括 Bapi： 從不同的 SAP 商務物件，在相同的 BAPI 交易中，您必須為 （使用相同的 WCF 用戶端） 的 RFC 作業叫用它們。</span><span class="sxs-lookup"><span data-stu-id="ed88e-141">If you want to include BAPIs from different SAP business objects in the same BAPI transaction, you must invoke them as RFC operations (using the same WCF client).</span></span> <span data-ttu-id="ed88e-142">您不能當做商務物件方法來叫用這些設定。</span><span class="sxs-lookup"><span data-stu-id="ed88e-142">You cannot invoke them as business object methods.</span></span>  
  
 <span data-ttu-id="ed88e-143">您可以呼叫 BAPI_TRANSACTION_COMMIT 或 BAPI_TRANSACTION_ROLLBACK 認可或復原 BAPI 交易上的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="ed88e-143">You call BAPI_TRANSACTION_COMMIT or BAPI_TRANSACTION_ROLLBACK to commit or roll back the BAPI transaction on the SAP system.</span></span> <span data-ttu-id="ed88e-144">配接器會呈現這些兩個 Bapi:</span><span class="sxs-lookup"><span data-stu-id="ed88e-144">The adapter surfaces these two BAPIs:</span></span>  
  
- <span data-ttu-id="ed88e-145">在以 RFC 作業的基礎節點。</span><span class="sxs-lookup"><span data-stu-id="ed88e-145">Under the Basis node as RFC operations.</span></span>  
  
- <span data-ttu-id="ed88e-146">在每個商務物件。</span><span class="sxs-lookup"><span data-stu-id="ed88e-146">Under each business object.</span></span>  
  
  <span data-ttu-id="ed88e-147">如需配接器上 SAP 所支援的 BAPI 交易的詳細資訊，請參閱[對 SAP 中的 Bapi 的作業](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="ed88e-147">For more information about how the adapter supports BAPI transactions on SAP, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).</span></span>  
  
## <a name="how-to-create-an-application-that-invokes-bapis-as-methods-of-business-objects"></a><span data-ttu-id="ed88e-148">如何建立應用程式叫用商務物件方法的 Bapi</span><span class="sxs-lookup"><span data-stu-id="ed88e-148">How to Create an Application that Invokes BAPIs as Methods of Business Objects</span></span>  
 <span data-ttu-id="ed88e-149">本節提供如何為商務物件的方法叫用 Bapi 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ed88e-149">This section provides information about how to invoke BAPIs as methods of business objects.</span></span> <span data-ttu-id="ed88e-150">在之後相同的基本程序時，應以 RFC 作業叫用 Bapi，不同之處在於您建立目標為 RFC 作業的 Bapi 的 WCF 用戶端，並用來叫用每個 BAPI。</span><span class="sxs-lookup"><span data-stu-id="ed88e-150">The same basic procedure should be followed to invoke BAPIs as RFC operations, except that you create a WCF client that targets the BAPIs as RFC operations and use it to invoke each BAPI.</span></span>  
  
 <span data-ttu-id="ed88e-151">若要建立 BAPI 的用戶端應用程式，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="ed88e-151">To create a BAPI client application, perform the following steps.</span></span>  
  
#### <a name="to-create-an-bapi-client-application"></a><span data-ttu-id="ed88e-152">若要建立 BAPI 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="ed88e-152">To create an BAPI client application</span></span>  
  
1. <span data-ttu-id="ed88e-153">產生 WCF 用戶端類別。</span><span class="sxs-lookup"><span data-stu-id="ed88e-153">Generate a WCF client class.</span></span> <span data-ttu-id="ed88e-154">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別 （或類別） 為目標的商務物件和您想要使用的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="ed88e-154">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF client class (or classes) that targets the business objects and BAPIs with which you want to work.</span></span> <span data-ttu-id="ed88e-155">請務必包含 BAPI_TRANSACTION_COMMIT 和公開的每個目標商務物件的 BAPI_TRANSACTION_ROLLBACK 方法 (Bapi)。</span><span class="sxs-lookup"><span data-stu-id="ed88e-155">Be sure to include the BAPI_TRANSACTION_COMMIT and the BAPI_TRANSACTION_ROLLBACK methods (BAPIs) exposed for each target business object.</span></span> <span data-ttu-id="ed88e-156">如需如何產生 WCF 用戶端的詳細資訊，請參閱[SAP 解決方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="ed88e-156">For more information about how to generate a WCF client, see [Generating a WCF Client or a WCF Service Contract for SAP Solution Artifacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).</span></span>  
  
2. <span data-ttu-id="ed88e-157">建立在步驟 1 所產生的 WCF 用戶端類別的執行個體以及建立和設定 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="ed88e-157">Create an instance of the WCF client class generated in step 1, and create and configure a WCF client.</span></span> <span data-ttu-id="ed88e-158">設定 WCF 用戶端包含指定的繫結和用戶端會使用的端點位址。</span><span class="sxs-lookup"><span data-stu-id="ed88e-158">Configuring the WCF client involves specifying the binding and endpoint address that the client will use.</span></span> <span data-ttu-id="ed88e-159">以命令方式在程式碼或是宣告式組態中，您可以這麼做。</span><span class="sxs-lookup"><span data-stu-id="ed88e-159">You can do this either imperatively in code or declaratively in configuration.</span></span> <span data-ttu-id="ed88e-160">如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統的設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="ed88e-160">For more information about how to specify a client binding, see [Configure a Client Binding for the SAP System](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md).</span></span> <span data-ttu-id="ed88e-161">下列程式碼會初始化銷售訂單 (BUS2032) SAP 商務物件，從設定 WCF 用戶端，並設定 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="ed88e-161">The following code initializes the WCF client for the Sales Order (BUS2032) SAP business object from configuration and sets the credentials for the SAP system.</span></span>  
  
   ```  
   BapiBUS2032Client bapiClient = new BapiBUS2032Client("SAPBinding_BapiBUS2032");  
  
   bapiClient.ClientCredentials.UserName.UserName = "YourUserName";  
   bapiClient.ClientCredentials.UserName.Password = "YourPassword";  
   ```  
  
3. <span data-ttu-id="ed88e-162">開啟 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="ed88e-162">Open the WCF client.</span></span>  
  
   ```  
   bapiClient.Open();  
   ```  
  
4. <span data-ttu-id="ed88e-163">叫用 WCF 用戶端上建立在步驟 2 中叫用適當的 Bapi SAP 系統上的方法。</span><span class="sxs-lookup"><span data-stu-id="ed88e-163">Invoke methods on the WCF client created in step 2 to invoke the appropriate BAPIs on the SAP system.</span></span> <span data-ttu-id="ed88e-164">您可以叫用多個 SAP 系統上的 Bapi。</span><span class="sxs-lookup"><span data-stu-id="ed88e-164">You can invoke multiple BAPIs on the SAP system.</span></span>  
  
5. <span data-ttu-id="ed88e-165">結束的交易：</span><span class="sxs-lookup"><span data-stu-id="ed88e-165">End the transaction by:</span></span>  
  
   1.  <span data-ttu-id="ed88e-166">叫用 BAPI_TRANSACTION_COMMIT; 方法來認可交易。</span><span class="sxs-lookup"><span data-stu-id="ed88e-166">Invoking the BAPI_TRANSACTION_COMMIT method to commit the transaction.</span></span>  
  
       ```  
       bapiClient.BAPI_TRANSACTION_COMMIT("X");  
       ```  
  
   2.  <span data-ttu-id="ed88e-167">叫用 BAPI_TRANSACTION_ROLLBACK 方法來回復交易。</span><span class="sxs-lookup"><span data-stu-id="ed88e-167">Invoking the BAPI_TRANSACTION_ROLLBACK method to roll back the transaction.</span></span>  
  
       ```  
       bapiClient.BAPI_TRANSACTION_ROLLBACK();  
       ```  
  
6. <span data-ttu-id="ed88e-168">關閉 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="ed88e-168">Close the WCF client.</span></span>  
  
   ```  
   bapiClient.Close();   
   ```  
  
### <a name="example"></a><span data-ttu-id="ed88e-169">範例</span><span class="sxs-lookup"><span data-stu-id="ed88e-169">Example</span></span>  
 <span data-ttu-id="ed88e-170">下列範例會叫用 CREATEFROMDAT2 BAPI 的銷售訂單的商務物件。</span><span class="sxs-lookup"><span data-stu-id="ed88e-170">The following example invokes the CREATEFROMDAT2 BAPI on the Sales Order business object.</span></span> <span data-ttu-id="ed88e-171">它會叫用 BAPI 數次，然後再叫用 BAPI_TRANSACTION_COMMIT 認可交易。</span><span class="sxs-lookup"><span data-stu-id="ed88e-171">It invokes the BAPI several times and then invokes BAPI_TRANSACTION_COMMIT to commit the transaction.</span></span> <span data-ttu-id="ed88e-172">如果發生錯誤時叫用 BAPI，BAPI_TRANSACTION_ROLLBACK 被用來回復交易的例外狀況處理常式叫用。</span><span class="sxs-lookup"><span data-stu-id="ed88e-172">If an error occurs when invoking the BAPI, BAPI_TRANSACTION_ROLLBACK is invoked in the exception handler to roll back the transaction.</span></span>  
  
 <span data-ttu-id="ed88e-173">CREATEFROMDAT2 方法接受許多參數;在範例中，為了簡潔起見已省略這些。</span><span class="sxs-lookup"><span data-stu-id="ed88e-173">The CREATEFROMDAT2 method takes many parameters; these are omitted in the example for the sake of brevity.</span></span> <span data-ttu-id="ed88e-174">您可以找到的範例，示範如何在 Microsoft 所隨附的範例中的 BAPI 交易[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ed88e-174">You can find a sample that demonstrates BAPI transactions in the samples shipped with the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="ed88e-175">如需詳細資訊，請參閱 <<c0> [ 適用於 SAP 配接器範例](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="ed88e-175">For more information, see [Samples for the SAP Adapter ](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed88e-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed88e-176">See Also</span></span>  
[<span data-ttu-id="ed88e-177">使用 WCF 服務模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="ed88e-177">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)  
 [<span data-ttu-id="ed88e-178">對 SAP 中的 Bapi 的作業</span><span class="sxs-lookup"><span data-stu-id="ed88e-178">Operations on BAPIs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)
---
title: "使用 WCF 服務模型的 SAP 中接收輸入的 tRFC 呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC calls, receiving inbound using the WCF service model
- WCF service model, receiving inbound tRFC calls
ms.assetid: 02dc282b-b659-466a-8bd1-f400a05f71ec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fb2091d0701831985a1975aa33bd5ecb667b443
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="f6b79-102">使用 WCF 服務模型的 SAP 中接收輸入的 tRFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="f6b79-102">Receive Inbound tRFC Calls in SAP using the WCF Service Model</span></span>
<span data-ttu-id="f6b79-103">您可以使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]為交易式 RFC (tRFC) 伺服器從 SAP 接收輸入的 tRFC 呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6b79-103">You can use the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as a transactional RFC (tRFC) server to receive inbound tRFC calls from SAP.</span></span> <span data-ttu-id="f6b79-104">針對傳入的 tRFCs[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援多個 tRFCs 中的工作 (LUW) 相同的 SAP 邏輯單元。</span><span class="sxs-lookup"><span data-stu-id="f6b79-104">For inbound tRFCs, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports multiple tRFCs in the same SAP logical unit of work (LUW).</span></span>  
  
 <span data-ttu-id="f6b79-105">本主題中的各節提供有關如何使用配接器做為 tRFC 伺服器 WCF 服務模型中的資訊。</span><span class="sxs-lookup"><span data-stu-id="f6b79-105">The sections in this topic provide information about how to use the adapter as a tRFC server in the WCF service model.</span></span>  
  
 <span data-ttu-id="f6b79-106">您可以找到有關使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]為 tRFC 伺服器中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="f6b79-106">You can find more information about using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as a tRFC server in the following topics:</span></span>  
  
-   <span data-ttu-id="f6b79-107">如需 tRFCs 上支援的概觀[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b79-107">For an overview of support for tRFCs on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span> <span data-ttu-id="f6b79-108">繼續之前，您應該閱讀本主題。</span><span class="sxs-lookup"><span data-stu-id="f6b79-108">You should read this topic before continuing.</span></span>  
  
-   <span data-ttu-id="f6b79-109">如需 tRFC 伺服器作業的訊息結構描述的詳細資訊，請參閱[tRFCs SAP 中的作業](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b79-109">For more information about the message schemas for tRFC server operations, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).</span></span>  
  
## <a name="the-wcf-service-contract-for-a-trfc"></a><span data-ttu-id="f6b79-110">TRFC 之 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="f6b79-110">The WCF Service Contract for a tRFC</span></span>  
 <span data-ttu-id="f6b79-111">您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生您想要從 SAP 系統接收 tRFCs WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="f6b79-111">You use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF service contract for the tRFCs that you want to receive from the SAP system.</span></span> <span data-ttu-id="f6b79-112">產生輸入的 tRFC 是類似於針對傳入的 RFC 產生的合約之處在於：</span><span class="sxs-lookup"><span data-stu-id="f6b79-112">The contract generated for an inbound tRFC is similar to that generated for an inbound RFC except that:</span></span>  
  
-   <span data-ttu-id="f6b79-113">tRFC 作業便會顯示一個 TRFC 節點下。</span><span class="sxs-lookup"><span data-stu-id="f6b79-113">tRFC operations are surfaced under the TRFC node.</span></span>  
  
-   <span data-ttu-id="f6b79-114">WCF 服務合約 （介面） 的內送 tRFCs 產生名為"Trfc"。</span><span class="sxs-lookup"><span data-stu-id="f6b79-114">The WCF service contract (interface) generated for incoming tRFCs is named "Trfc".</span></span> <span data-ttu-id="f6b79-115">當您將服務端點加入至服務主機，您必須指定此介面。</span><span class="sxs-lookup"><span data-stu-id="f6b79-115">You must specify this interface when you add the service endpoint to the service host.</span></span> <span data-ttu-id="f6b79-116">這也是 WCF 服務必須實作的介面。</span><span class="sxs-lookup"><span data-stu-id="f6b79-116">This is also the interface that your WCF service must implement.</span></span>  
  
    ```  
    public interface Trfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Trfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Trfc/Z_RFC_MKD_ADD/response")]  
        Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
    }  
    ```  
  
-   <span data-ttu-id="f6b79-117">TRFC 作業的要求訊息合約都具有 GUID 參數。</span><span class="sxs-lookup"><span data-stu-id="f6b79-117">The request message contract for TRFC operations has a GUID parameter.</span></span> <span data-ttu-id="f6b79-118">這是對應至 SAP TID tRFC 的 GUID。</span><span class="sxs-lookup"><span data-stu-id="f6b79-118">This is the GUID that maps to the SAP TID for the tRFC.</span></span> <span data-ttu-id="f6b79-119">TRFC 伺服器作業中，配接器會管理所有的呼叫認可、 復原，並確認 TID SAP 系統，所以沒有理由要明確地使用此 GUID。</span><span class="sxs-lookup"><span data-stu-id="f6b79-119">In tRFC server operations, the adapter manages all calls to commit, rollback, and confirm the TID by the SAP system so there is no reason for you to explicitly use this GUID.</span></span> <span data-ttu-id="f6b79-120">不過，可以用它來擷取從 SAP TID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]藉由呼叫**SapAdapterUtilities.ConvertGuidToTid**。</span><span class="sxs-lookup"><span data-stu-id="f6b79-120">However, you can use it to retrieve the SAP TID from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] by calling **SapAdapterUtilities.ConvertGuidToTid**.</span></span> <span data-ttu-id="f6b79-121">這可協助您疑難排解 SAP 系統上的問題。</span><span class="sxs-lookup"><span data-stu-id="f6b79-121">This can be useful to help you troubleshoot issues on the SAP system.</span></span>  
  
    ```  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
    [System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Trfc/", IsWrapped=true)]  
    public partial class Z_RFC_MKD_ADDRequest {  
  
        ...  
  
        public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y, System.Guid TransactionalRfcOperationIdentifier) {  
            this.DEST = DEST;  
            this.X = X;  
            this.Y = Y;  
            this.TransactionalRfcOperationIdentifier = TransactionalRfcOperationIdentifier;  
        }  
    }  
  
    ```  
  
## <a name="how-do-i-enable-the-adapter-to-act-as-a-trfc-server"></a><span data-ttu-id="f6b79-122">如何為 tRFC 伺服器中啟用 Act 配接器？</span><span class="sxs-lookup"><span data-stu-id="f6b79-122">How do I Enable the Adapter to Act as a tRFC Server?</span></span>  
 <span data-ttu-id="f6b79-123">若要啟用配接器做為 tRFC 伺服器，您必須設定**TidDatabaseConnectionString**屬性繫結至 TID 資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="f6b79-123">To enable the adapter to act as a tRFC server, you must set the **TidDatabaseConnectionString** binding property to the connection string for the TID database.</span></span> <span data-ttu-id="f6b79-124">開啟服務主機之前，您應該這麼做。</span><span class="sxs-lookup"><span data-stu-id="f6b79-124">You should do this before you open the service host.</span></span> <span data-ttu-id="f6b79-125">這是配接器會儲存每個 tRFC SAP 交易識別碼 (TID) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f6b79-125">This is the database in which the adapter stores the SAP transaction ID (TID) for each tRFC.</span></span> <span data-ttu-id="f6b79-126">如需此繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b79-126">For more information about this binding property, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
## <a name="how-do-i-enlist-in-the-transaction-for-inbound-trfcs"></a><span data-ttu-id="f6b79-127">如何將在輸入 tRFCs 的交易中編列？</span><span class="sxs-lookup"><span data-stu-id="f6b79-127">How do I Enlist in the Transaction for Inbound tRFCs?</span></span>  
 <span data-ttu-id="f6b79-128">SAP 邏輯單元的工作 (LUW) 可以包含多個 tRFCs。</span><span class="sxs-lookup"><span data-stu-id="f6b79-128">An SAP Logical Unit of Work (LUW) can contain multiple tRFCs.</span></span> <span data-ttu-id="f6b79-129">SAP 系統上 LUW 識別的唯一交易識別碼 (TID)。</span><span class="sxs-lookup"><span data-stu-id="f6b79-129">On the SAP system a LUW is identified by a unique Transaction ID (TID).</span></span> <span data-ttu-id="f6b79-130">配接器會針對每一個 SAP 系統時它會叫用的介面卡上 tRFC 呼叫使用 TIDs 建立可認可的交易。</span><span class="sxs-lookup"><span data-stu-id="f6b79-130">The adapter creates a committable transaction for each of the TIDs that the SAP system uses when it invokes tRFC calls on the adapter.</span></span> <span data-ttu-id="f6b79-131">當 SAP 系統叫用的介面卡; tRFC配接器會與 SAP TID 到您的服務相關聯的異動流動。</span><span class="sxs-lookup"><span data-stu-id="f6b79-131">When the SAP system invokes a tRFC on the adapter; the adapter flows the transaction associated with the SAP TID to your service.</span></span> <span data-ttu-id="f6b79-132">您可以存取此交易成為環境交易作業方法內。</span><span class="sxs-lookup"><span data-stu-id="f6b79-132">You can access this transaction as the ambient transaction from inside your operation method.</span></span> <span data-ttu-id="f6b79-133">在此環境異動中登記，在作業中執行的動作便可以參與 SAP LUW。</span><span class="sxs-lookup"><span data-stu-id="f6b79-133">By enlisting in this ambient transaction, the actions performed in the operation can participate in the SAP LUW.</span></span>  
  
 <span data-ttu-id="f6b79-134">若要在作業方法中的環境異動中登記，您必須：</span><span class="sxs-lookup"><span data-stu-id="f6b79-134">To enlist in the ambient transaction in an operation method, you must:</span></span>  
  
1.  <span data-ttu-id="f6b79-135">使用作業方法加上註解**TransactionScopeRequired**屬性**OperationBehavior**屬性。</span><span class="sxs-lookup"><span data-stu-id="f6b79-135">Annotate the operation method with the **TransactionScopeRequired** property of the **OperationBehavior** attribute.</span></span> <span data-ttu-id="f6b79-136">這會告知 WCF 您想要從作業內的環境交易存取。</span><span class="sxs-lookup"><span data-stu-id="f6b79-136">This tells WCF that you want access to the ambient transaction from inside the operation.</span></span>  
  
2.  <span data-ttu-id="f6b79-137">建立交易範圍加上附註與操作方法**TransactionAutoComplete**屬性**OperationBehavior**屬性或明確地使用**TransactionScope**作業方法內。</span><span class="sxs-lookup"><span data-stu-id="f6b79-137">Create a transaction scope either by annotating the operation method with the **TransactionAutoComplete** property of the **OperationBehavior** attribute or by explicitly using a **TransactionScope** inside the operation method.</span></span>  
  
 <span data-ttu-id="f6b79-138">下列範例會示範實作兩個作業的服務。</span><span class="sxs-lookup"><span data-stu-id="f6b79-138">The following example shows a service that implements two operations.</span></span> <span data-ttu-id="f6b79-139">這兩種作業的方法必須標註**TransactionScopeRequired**屬性來存取環境交易。</span><span class="sxs-lookup"><span data-stu-id="f6b79-139">Both operation methods are annotated with the **TransactionScopeRequired** property to access the ambient transaction.</span></span>  
  
-   <span data-ttu-id="f6b79-140">**Z_TRFC_EXAMPLE1**明確登記在交易中使用**TransactionScope**物件。</span><span class="sxs-lookup"><span data-stu-id="f6b79-140">**Z_TRFC_EXAMPLE1** explicitly enlists in the transaction by using a **TransactionScope** object.</span></span>  
  
-   <span data-ttu-id="f6b79-141">**Z_TRFC_EXAMPLE2**附註**TransactionAutoComplete**登記在交易中的屬性</span><span class="sxs-lookup"><span data-stu-id="f6b79-141">**Z_TRFC_EXAMPLE2** is annotated with the **TransactionAutoComplete** property to enlist in the transaction</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, UseSynchronizationContext = false)]  
class Z_Example_ServiceContractClass : Trfc  
{  
  
    // This operation method explicitly creates a TransactionScope to enlist in the ambient transaction  
    // You must explictly call ts.Complete to complete the transaction before you return from the operation  
    // Otherwise the transaction is aborted.  
    // You can throw an exception or return without calling ts.complete to abort the transacation  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public Z_TRFC_EXAMPLE1Response Z_TRFC_EXAMPLE1(Z_TRFC_EXAMPLE1Request request)  
    {  
        using (TransactionScope ts = new TransactionScope(TransactionScopeOption.Required))  
        {  
            // Process tRFC  
  
            ...  
  
            Z_TRFC_EXAMPLE1Response response = new Z_TRFC_EXAMPLE1Response();  
            response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
            return response;  
            //since there is no ts.Complete(), this is equivalent to a rollback.  
        }  
    }  
  
    // This operation method sets the TransactionAutoComplete property of the OperationBehavior attribute  
    // to enlist in the transaction. There is no need to explictly create a TransactionScope in the code.  
    // If the method returns with no unhandled exceptions, the transaction completes; otherwise it aborts  
    // You can throw an exception to abort the transaction.  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public Z_TRFC_EXAMPLE2Response Z_TRFC_EXAMPLE2(Z_TRFC_EXAMPLE2Request request)  
    {  
        // Process tRFC  
  
        ...  
  
        Z_TRFC_EXAMPLE2Response response = new Z_TRFC_EXAMPLE2Response();  
        response.TransactionalRfcOperationIdentifier = request.TransactionalRfcOperationIdentifier;  
        return response;  
        //if there is no unhandled exception, the transaction completes when the operation returns.  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6b79-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6b79-142">See Also</span></span>  
[<span data-ttu-id="f6b79-143">開發應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="f6b79-143">Develop applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)
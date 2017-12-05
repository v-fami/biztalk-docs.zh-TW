---
title: "接收來自 SAP 系統使用 WCF 通道模型的輸入的操作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming inbound flat-file IDOCs
- WCF channel model, receiving inbound operations from the SAP system
- WCF channel model, raising an exception
ms.assetid: d71d0537-fda4-44ab-85dc-6e27aad23caf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b76ae42cf0ffc26b818e35d83f59e64158b923a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model"></a><span data-ttu-id="d0dc2-102">接收來自 SAP 系統使用 WCF 通道模型的輸入的操作</span><span class="sxs-lookup"><span data-stu-id="d0dc2-102">Receive Inbound Operations from the SAP System Using the WCF Channel Model</span></span>
<span data-ttu-id="d0dc2-103">做為 RFC 伺服器，並接收 SAP 系統 （例如傳送 IDOC，或叫用 RFC） 叫用的作業，您必須建立通道接聽程式可以接聽來自 SAP 程式 ID 的訊息，透過**System.ServiceModel.Channels.IReplyChannel**通道圖案。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-103">To act as an RFC server and receive operations invoked by the SAP system (such as sending an IDOC or invoking an RFC), you must create a channel listener that can listen for messages from a SAP Program ID over a **System.ServiceModel.Channels.IReplyChannel** channel shape.</span></span>  
  
 <span data-ttu-id="d0dc2-104">通道接聽程式 (**System.ServiceModel.Channels.IChannelListener**) 是可用來從特定的 WCF 端點接收訊息的 WCF 通訊物件。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-104">A channel listener (**System.ServiceModel.Channels.IChannelListener**) is a WCF communication object that can be used to receive messages from specific WCF endpoints.</span></span> <span data-ttu-id="d0dc2-105">通道接聽程式做為您可以從中建立在其上叫用用戶端 （SAP 系統） 的訊息可以接收您的服務的通道處理站。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-105">The channel listener functions as a factory from which you can create channels over which messages invoked by a client (the SAP system) can be received by your service.</span></span> <span data-ttu-id="d0dc2-106">建立通道接聽項所從**Microsoft.Adapters.SAP.SAPBinding**物件叫用**BuildChannelListener**方法。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-106">You create a channel listener by from a **Microsoft.Adapters.SAP.SAPBinding** object by invoking the **BuildChannelListener** method.</span></span> <span data-ttu-id="d0dc2-107">您提供的 SAP 連接指定的輸入的操作將會收到這個方法的 SAP 程式 ID URI。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-107">You supply an SAP connection URI that specifies the SAP Program ID from which inbound operations will be received to this method.</span></span>  
  
 <span data-ttu-id="d0dc2-108">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援**IReplyChannel**通道圖案。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-108">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the **IReplyChannel** channel shape.</span></span> <span data-ttu-id="d0dc2-109">**IReplyChannel**通道支援傳入的要求-回應訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-109">**IReplyChannel** channels support an inbound request-response message exchange pattern.</span></span> <span data-ttu-id="d0dc2-110">也就是說，外部程式在其中透過通道和程式傳送要求訊息的模式會傳回的回應。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-110">That is, a pattern in which an external program sends a request message over the channel and your program returns a response.</span></span>  
  
 <span data-ttu-id="d0dc2-111">如需如何接收作業使用的概觀**IReplyChannel**在 WCF 中，請參閱[服務通道層級程式設計](https://msdn.microsoft.com/library/ms789029.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-111">For an overview of how to receive operations using an **IReplyChannel** in WCF, see [Service Channel-Level Programming](https://msdn.microsoft.com/library/ms789029.aspx).</span></span>
  
 <span data-ttu-id="d0dc2-112">本章節涵蓋下列主題所特有的 SAP 系統從接收作業：</span><span class="sxs-lookup"><span data-stu-id="d0dc2-112">This section covers the following topics that are specific to receiving operations from a SAP system:</span></span>  
  
-   <span data-ttu-id="d0dc2-113">如何篩選針對特定作業使用的通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-113">How to filter for specific operations using the channel listener.</span></span>  
  
-   <span data-ttu-id="d0dc2-114">如何引發例外狀況 SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-114">How to raise an exception on the SAP system.</span></span>  
  
-   <span data-ttu-id="d0dc2-115">SAP 配接器從輸入的一般檔案 Idoc 的串流處理。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-115">Streaming inbound flat-file IDOCs from the SAP adapter.</span></span>  
  
-   <span data-ttu-id="d0dc2-116">如何從 SAP 系統接收作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-116">How to receive operations from the SAP system.</span></span>  
  
## <a name="how-do-i-filter-operations-using-the-channel-listener"></a><span data-ttu-id="d0dc2-117">我要如何篩選使用的通道接聽程式的作業？</span><span class="sxs-lookup"><span data-stu-id="d0dc2-117">How Do I Filter Operations Using the Channel Listener?</span></span>  
  
### <a name="using-an-inboundactioncollection-to-filter-operations"></a><span data-ttu-id="d0dc2-118">若要篩選作業中使用 InboundActionCollection</span><span class="sxs-lookup"><span data-stu-id="d0dc2-118">Using an InboundActionCollection to Filter Operations</span></span>  
 <span data-ttu-id="d0dc2-119">[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供**Microsoft.ServiceModel.Channels.InboundActionCollection**類別，讓您篩選是由通道接聽程式收到並且傳遞給應用程式程式碼的作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-119">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides the **Microsoft.ServiceModel.Channels.InboundActionCollection** class to enable you to filter operations that are received by a channel listener and passed to your application code.</span></span> <span data-ttu-id="d0dc2-120">若要篩選針對特定作業，您可以建立這個類別的執行個體使用接聽程式端點 URI。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-120">To filter for specific operations, you create an instance of this class by using the listener endpoint URI.</span></span> <span data-ttu-id="d0dc2-121">然後您加入至集合的每個目標作業 （要求） 訊息動作。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-121">Then you add the (request) message action for each target operation to the collection.</span></span> <span data-ttu-id="d0dc2-122">最後，您會加入輸入的動作集合，以便**System.ServiceModel.Channels.BindingParameterCollection**物件，然後將此繫結參數集合傳遞至建立通道接聽程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-122">Finally, you add the inbound action collection to a **System.ServiceModel.Channels.BindingParameterCollection** object and then pass this binding parameter collection into the call to create the channel listener.</span></span>  
  
 <span data-ttu-id="d0dc2-123">如果 SAP 系統會叫用不是輸入的動作集合中的作業：</span><span class="sxs-lookup"><span data-stu-id="d0dc2-123">If the SAP system invokes an operation that is not in the inbound action collection:</span></span>  
  
-   <span data-ttu-id="d0dc2-124">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]傳回呼叫者的例外狀況的例外狀況，在 SAP 系統，並出現下列訊息: 「 未處理連入的 RFC 呼叫 [RFC_NAME] Rfc 伺服器上 」。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-124">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] returns an EXCEPTION exception to the caller on the SAP system with the following message: "The incoming RFC call [RFC_NAME] on the Rfc Server is not handled".</span></span> <span data-ttu-id="d0dc2-125">此訊息，請在 [RFC_NAME] 是 RFC (例如，IDOC_INBOUND_ASYNCHRONOUS) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-125">In this message, [RFC_NAME] is the name of the RFC (for example, IDOC_INBOUND_ASYNCHRONOUS).</span></span>  
  
-   <span data-ttu-id="d0dc2-126">配接器會擲回**Microsoft.ServiceModel.Channels.Common.AdapterException**以訊息，表示已收到的作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-126">The adapter throws a **Microsoft.ServiceModel.Channels.Common.AdapterException** with a message that indicates the operation that was received.</span></span> <span data-ttu-id="d0dc2-127">如需如何使用這個例外狀況的範例，請參閱本主題結尾處的範例。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-127">For an example of how to use this exception, see the example at the end of this topic.</span></span>  
  
 <span data-ttu-id="d0dc2-128">下列程式碼範例示範如何使用**InboundActionCollection**建立通道接聽程式的單一 RFC，Z_RFC_MKD_DIV 篩選。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-128">The following code example shows how to use an **InboundActionCollection** to create a channel listener that filters for a single RFC, Z_RFC_MKD_DIV.</span></span>  
  
```  
// The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
// and credentials.  
Uri listeneraddress =  
    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
// Create a binding and set AcceptCredentialsInUri to true  
SAPBinding binding = new SAPBinding();  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying the binding parameter collection (to filter for the Z_RFC_MKD_DIV action)  
listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
```  
  
### <a name="manually-filtering-operations"></a><span data-ttu-id="d0dc2-129">手動篩選作業</span><span class="sxs-lookup"><span data-stu-id="d0dc2-129">Manually Filtering Operations</span></span>  
 <span data-ttu-id="d0dc2-130">如果您沒有指定之通道接聽程式的輸入的動作集合，則會在您的程式碼傳遞由 SAP 系統所叫用的所有作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-130">If you do not specify an inbound action collection for the channel listener, then all operations invoked by the SAP system will be passed to your code.</span></span> <span data-ttu-id="d0dc2-131">您可以手動篩選這類作業，藉由檢查傳入要求的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-131">You can manually filter such operations by checking the message action of inbound requests.</span></span>  
  
 <span data-ttu-id="d0dc2-132">也可能想要篩選其內容為基礎的運算中的案例。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-132">There may also be scenarios in which you want to filter an operation based on its content.</span></span> <span data-ttu-id="d0dc2-133">如果您收到的 Idoc 中的範例：</span><span class="sxs-lookup"><span data-stu-id="d0dc2-133">For example if you are receiving IDOCs in:</span></span>  
  
-   <span data-ttu-id="d0dc2-134">字串格式 ( **ReceiveIDocFormat**繫結屬性是**字串**)，則所有使用 ReceiveIdoc 作業接收 Idoc。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-134">String format (the **ReceiveIDocFormat** binding property is **String**); all IDOCs are received using the ReceiveIdoc operation.</span></span>  
  
-   <span data-ttu-id="d0dc2-135">Rfc 格式 ( **ReceiveIDocFormat**繫結屬性是**Rfc**)，則所有使用 IDOC_INBOUND_ASYNCHRONOUS RFC 或 INBOUND_IDOC_PROCESS RFC 接收 Idoc。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-135">Rfc format (the **ReceiveIDocFormat** binding property is **Rfc**); all IDOCs are received using either the IDOC_INBOUND_ASYNCHRONOUS RFC or the INBOUND_IDOC_PROCESS RFC.</span></span>  
  
 <span data-ttu-id="d0dc2-136">在此案例中您可能想要實作篩選根據特定 IDOC 中的參數 （例如 IDOC 類型） 您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-136">In this scenario you may want to implement filtering based on specific IDOC parameters (such as the IDOC type) in your code.</span></span>  
  
 <span data-ttu-id="d0dc2-137">當您手動篩選作業時，您可以傳回錯誤，以[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]未處理的作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-137">When you filter operations manually, you can return a fault to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for operations that you don't handle.</span></span> <span data-ttu-id="d0dc2-138">這會引發例外狀況例外狀況至呼叫端 SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-138">This will raise the EXCEPTION exception to the caller on the SAP System.</span></span> <span data-ttu-id="d0dc2-139">如果您不想要引發 SAP 時發生例外狀況，您也可以傳回空白回應。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-139">You can also return an empty response if you don't want to raise an exception on SAP.</span></span>  
  
 <span data-ttu-id="d0dc2-140">下列程式碼會示範如何以手動方式篩選 Z_RFC_MKD_DIV 作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-140">The following code shows how to filter manually for the Z_RFC_MKD_DIV operation.</span></span>  
  
```  
// Get the message from the channel  
RequestContext rc = channel.ReceiveRequest();  
Message reqMessage = rc.RequestMessage;  
  
// Filter based on the message action.  
if (reqMessage.Headers.Action == "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV")  
{  
  
    // Process message and return response.  
    ...  
  
}  
else  
{  
    // If this isn't the correct message return an empty response or a fault message.  
    // This example returns an empty response.  
    rc.Reply(Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response"));  
}  
```  
  
## <a name="how-do-i-raise-an-exception-on-the-sap-system"></a><span data-ttu-id="d0dc2-141">我要如何引發例外狀況上 SAP 系統？</span><span class="sxs-lookup"><span data-stu-id="d0dc2-141">How Do I Raise an Exception on the SAP System?</span></span>  
 <span data-ttu-id="d0dc2-142">若要表示至 SAP 系統上呼叫端錯誤來回覆要求訊息，並且產生 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-142">To indicate an error to the caller on the SAP system you can reply to a request message with a SOAP fault.</span></span> <span data-ttu-id="d0dc2-143">當您傳回 SOAP 錯誤以[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，配接器 SAP 系統上會發生例外狀況的例外狀況傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-143">When you return a SOAP fault to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], the adapter returns an EXCEPTION exception to the caller on the SAP system.</span></span> <span data-ttu-id="d0dc2-144">例外狀況訊息是從 SOAP 錯誤的項目建立的。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-144">The exception message is created from the elements of the SOAP fault.</span></span>  
  
 <span data-ttu-id="d0dc2-145">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 例外狀況，依照下列順序的優先順序會建立訊息：</span><span class="sxs-lookup"><span data-stu-id="d0dc2-145">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] creates the message for the SAP EXCEPTION according to the following order of precedence:</span></span>  
  
1.  <span data-ttu-id="d0dc2-146">SOAP 錯誤中包含詳細資料物件，如果配接器將序列化為字串的詳細資料，並設定例外狀況訊息為此字串。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-146">If the SOAP fault contains a detail object, the adapter serializes the detail to a string and the exception message is set to this string.</span></span>  
  
2.  <span data-ttu-id="d0dc2-147">如果 SOAP 錯誤中包含的原因，例外狀況訊息是設定為它的值。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-147">If the SOAP fault contains a reason, the exception message is set to its value.</span></span>  
  
3.  <span data-ttu-id="d0dc2-148">否則，將配接器序列化**MessageFault**字串和例外狀況訊息的物件本身會設為此字串。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-148">Otherwise, the adapter serializes the **MessageFault** object itself to a string and the exception message is set to this string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0dc2-149">配接器只能建立傳回 SAP 系統; 所引發的例外狀況的例外狀況訊息使用錯誤訊息因此，您為這些實體的值是完全由您。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-149">The adapter only uses the fault message to create the exception message returned in the exception raised on the SAP system; therefore, the values that you set for these entities is completely up to you.</span></span>  
  
 <span data-ttu-id="d0dc2-150">WCF 提供**System.ServiceModel.Channels.MessageFault**類別來封裝在記憶體中的表示 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-150">WCF provides the **System.ServiceModel.Channels.MessageFault** class to encapsulate an in-memory representation of a SOAP fault.</span></span> <span data-ttu-id="d0dc2-151">您可以使用任何靜態、 多載**MessageFault.CreateFault**方法來建立新的 SOAP 錯誤，您可以再建立錯誤訊息藉由叫用適當**Message.CreateMessage**多載。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-151">You can use any of the static, overloaded **MessageFault.CreateFault** methods to create a new SOAP fault from which you can then create a fault message by invoking the appropriate **Message.CreateMessage** overload.</span></span> <span data-ttu-id="d0dc2-152">WCF 還提供的多載**CreateMessage**所建立的錯誤訊息，而不使用**MessageFault**物件。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-152">WCF also provides overloads of **CreateMessage** that create a fault message without using a **MessageFault** object.</span></span>  
  
 <span data-ttu-id="d0dc2-153">您使用**System.ServiceModel.Channels.RequestContext.Reply**方法傳回的錯誤訊息給配接器。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-153">You use the **System.ServiceModel.Channels.RequestContext.Reply** method to return the fault message to the adapter.</span></span> <span data-ttu-id="d0dc2-154">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]會忽略錯誤訊息的訊息動作，因此您可以設定任何值的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-154">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ignores the message action for fault messages, so you can set the message action to any value.</span></span>  
  
 <span data-ttu-id="d0dc2-155">下列範例示範如何傳回錯誤訊息[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-155">The following example shows how to return a fault message to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="d0dc2-156">這個範例省略了建立的通道接聽程式和通道的步驟。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-156">This example omits the steps to create the channel listener and channel.</span></span>  
  
```  
RequestContext rc = channel.ReceiveRequest();  
…  
// Start processing the inbound message  
…  
// If an error is encountered return a fault to the SAP system  
// This example uses CreateMessage overload to create a fault message.  
// The overload takes a SOAP version, fault code, reason, and message action  
// The SAP adapter ignores the message action for a fault so you can set it to any value you want.   
Message faultMessage = Message.CreateMessage(MessageVersion.Default, new FaultCode("SAP Example Fault"), "Testing SAP Faults", rc.RequestMessage.Headers.Action + "/fault");  
  
rc.Reply(faultMessage);  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-sap-adapter"></a><span data-ttu-id="d0dc2-157">SAP 配接器從資料流輸入的一般檔案 Idoc</span><span class="sxs-lookup"><span data-stu-id="d0dc2-157">Streaming Inbound Flat-File IDOCs from the SAP Adapter</span></span>  
 <span data-ttu-id="d0dc2-158">您會收到一般檔案 （字串） 的 Idoc 傳入 ReceiveIdoc 作業中的配接器。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-158">You receive flat-file (string) IDOCs from the adapter in the inbound ReceiveIdoc operation.</span></span> <span data-ttu-id="d0dc2-159">IDOC 資料會以這項作業中的單一節點下的字串表示。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-159">The IDOC data is represented as a string under a single node in this operation.</span></span> <span data-ttu-id="d0dc2-160">基於這個理由，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]支援節點值的資料流處理的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-160">For this reason, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports node-value streaming on the request message.</span></span> <span data-ttu-id="d0dc2-161">若要執行的節點值的資料流，您必須使用 ReceiveIdoc 作業的要求訊息，藉由叫用**Message.WriteBodyContents**方法**System.Xml.XmlDictionaryWriter** ，為能串流 IDOC 資料。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-161">To perform node-value streaming, you must consume the request message for the ReceiveIdoc operation by invoking the **Message.WriteBodyContents** method with a **System.Xml.XmlDictionaryWriter** that is capable of streaming the IDOC data.</span></span> <span data-ttu-id="d0dc2-162">如需如何執行這項操作資訊，請參閱[SAP 使用 WCF 通道模型中的資料流處理一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-162">For information about how to do this, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="how-do-i-receive-operations-from-a-sap-system-using-an-ireplychannel"></a><span data-ttu-id="d0dc2-163">如何在使用 IReplyChannel 的 SAP 系統從接收作業？</span><span class="sxs-lookup"><span data-stu-id="d0dc2-163">How Do I Receive Operations from a SAP System Using an IReplyChannel?</span></span>  
 <span data-ttu-id="d0dc2-164">若要從 SAP 系統接收作業，使用 WCF 通道模型，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-164">To receive operations from a SAP system by using the WCF channel model, perform the following steps.</span></span>  
  
#### <a name="to-receive-operations-from-the-sap-system-using-an-ireplychannel"></a><span data-ttu-id="d0dc2-165">若要從使用 IReplyChannel SAP 系統接收作業</span><span class="sxs-lookup"><span data-stu-id="d0dc2-165">To receive operations from the SAP system using an IReplyChannel</span></span>  
  
1.  <span data-ttu-id="d0dc2-166">建立的執行個體**SAPBinding**並設定您想要接收的作業所需的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-166">Create an instance of **SAPBinding** and set the binding properties required to for the operations you want to receive.</span></span> <span data-ttu-id="d0dc2-167">您必須設定至少**AcceptCredentialsInUri**繫結屬性為 true。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-167">At a minimum you must set the **AcceptCredentialsInUri** binding property to true.</span></span> <span data-ttu-id="d0dc2-168">若要做為 tRFC 伺服器，您必須設定**TidDatabaseConnectionString**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-168">To act as a tRFC server, you must set the **TidDatabaseConnectionString** binding property.</span></span> <span data-ttu-id="d0dc2-169">如需繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for mySAP Business Suite 繫結屬性](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-169">For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).</span></span>  
  
    ```  
    SAPBinding binding = new SAPBinding();  
    binding.AcceptCredentialsInUri = true;  
    ```  
  
2.  <span data-ttu-id="d0dc2-170">建立**BindingParameterCollection**並加入**InboundActionCollection** ，其中包含您想要接收的作業動作。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-170">Create a **BindingParameterCollection** and add an **InboundActionCollection** that contains the actions of the operations that you want to receive.</span></span> <span data-ttu-id="d0dc2-171">配接器會將例外狀況傳回至 SAP 系統的所有其他作業。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-171">The adapter will return an exception to the SAP system for all other operations.</span></span> <span data-ttu-id="d0dc2-172">此步驟是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-172">This step is optional.</span></span> <span data-ttu-id="d0dc2-173">如需詳細資訊，請參閱[接收輸入作業使用 WCF 通道模型之 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-173">For more information, see [Receiving Inbound Operations from the SAP System Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
    ```  
    InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
    actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
    BindingParameterCollection bpcol = new BindingParameterCollection();  
    bpcol.Add(actions);  
    ```  
  
3.  <span data-ttu-id="d0dc2-174">叫用來建立通道接聽程式**BuildChannelListener < IReplyChannel\>** 方法**SAPBinding**並開啟它。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-174">Create a channel listener by invoking **BuildChannelListener<IReplyChannel\>** method on the **SAPBinding** and open it.</span></span> <span data-ttu-id="d0dc2-175">您可以指定 SAP 連線 URI 為其中一個參數，這個方法。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-175">You specify the SAP connection URI as one of the parameters to this method.</span></span> <span data-ttu-id="d0dc2-176">連線 URI 必須包含參數的 RFC 目的地 SAP 系統上。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-176">The connection URI must contain parameters for an RFC Destination on the SAP system.</span></span> <span data-ttu-id="d0dc2-177">如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-177">For more information about the SAP connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span> <span data-ttu-id="d0dc2-178">如果您建立**BindingParameterCollection**在步驟 3 中，您也指定這當建立通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-178">If you created a **BindingParameterCollection** in step 3, you also specify this when you create the channel listener.</span></span>  
  
    ```  
    Uri listeneraddress =  
        new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
    IChannelListener<IReplyChannel> listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, bpcol);  
    listener.Open();  
    ```  
  
4.  <span data-ttu-id="d0dc2-179">取得**IReplyChannel**叫用的通道**AcceptChannel**接聽程式上的方法，並開啟它。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-179">Get an **IReplyChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IReplyChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
5.  <span data-ttu-id="d0dc2-180">叫用**ReceiveRequest**上從配接器取得下一項作業的要求訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-180">Invoke **ReceiveRequest** on the channel to get the request message for the next operation from the adapter.</span></span>  
  
    ```  
    RequestContext rc = channel.ReceiveRequest();  
    ```  
  
6.  <span data-ttu-id="d0dc2-181">使用配接器傳送要求訊息。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-181">Consume the request message sent by the adapter.</span></span> <span data-ttu-id="d0dc2-182">取得要求訊息從**RequestMessage**屬性**RequestContext**。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-182">You get the request message from the **RequestMessage** property of the **RequestContext**.</span></span> <span data-ttu-id="d0dc2-183">您可以使用訊息使用**XmlReader**或**XmlDictionaryWriter**。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-183">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = (XmlReader)rc.RequestMessage.GetReaderAtBodyContents();  
    ```  
  
7.  <span data-ttu-id="d0dc2-184">完成此作業藉由傳回至 SAP 系統的回應或錯誤：</span><span class="sxs-lookup"><span data-stu-id="d0dc2-184">Complete the operation by returning a response or fault to the SAP system:</span></span>  
  
    1.  <span data-ttu-id="d0dc2-185">處理訊息，並將回應傳回至 SAP 系統的回應訊息傳回至配接器。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-185">Process the message and return a response to the SAP system by returning the response message to the adapter.</span></span> <span data-ttu-id="d0dc2-186">這個範例會傳回空的訊息。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-186">This example returns an empty message.</span></span>  
  
        ```  
        respMessage = Message.CreateMessage(MessageVersion.Default, rc.RequestMessage.Headers.Action + "/response");  
        rc.Reply(respMessage);  
        ```  
  
    2.  <span data-ttu-id="d0dc2-187">返回 SAP 系統的例外狀況所傳回的錯誤訊息給配接器。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-187">Return an exception to the SAP system by returning a fault message to the adapter.</span></span> <span data-ttu-id="d0dc2-188">您可以使用任何值的訊息動作、 錯誤碼和原因。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-188">You can use any value for the message action, fault code, and reason.</span></span>  
  
        ```  
        MessageFault fault = MessageFault.CreateFault(new FaultCode("ProcFault"), "Processing Error");  
        Message respMessage = Message.CreateMessage(MessageVersion.Default, fault, String.Empty);  
        rc.Reply(respMessage);  
        ```  
  
8.  <span data-ttu-id="d0dc2-189">在送出訊息之後，請關閉要求內容。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-189">Close the request context after you have sent the message.</span></span>  
  
    ```  
    rc.Close();  
    ```  
  
9. <span data-ttu-id="d0dc2-190">當您完成處理要求，請關閉通道。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-190">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d0dc2-191">處理作業完成之後，您必須關閉通道。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-191">You must close the channel after you have finished processing the operation.</span></span> <span data-ttu-id="d0dc2-192">無法關閉通道可能會影響您的程式碼的行為。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-192">Failure to close the channel may affect the behavior of your code.</span></span>  
  
10. <span data-ttu-id="d0dc2-193">當您完成從 SAP 系統接收作業時，請關閉接聽程式。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-193">Close the listener when you are finished receiving operations from the SAP system.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d0dc2-194">當您完成時，您必須明確地關閉接聽程式使用。否則，您的程式可能無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-194">You must explicitly close the listener when you are done using it; otherwise, your program may not behave properly.</span></span> <span data-ttu-id="d0dc2-195">關閉接聽程式不會關閉建立使用接聽程式通道。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-195">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="d0dc2-196">您必須同時也可以明確關閉使用接聽程式所建立的每個通道。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-196">You must also explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0dc2-197">範例</span><span class="sxs-lookup"><span data-stu-id="d0dc2-197">Example</span></span>  
 <span data-ttu-id="d0dc2-198">下列範例接收 RFC，SAP 系統從 Z_RFC_MKD_DIV。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-198">The following example receives an RFC, Z_RFC_MKD_DIV from the SAP system.</span></span> <span data-ttu-id="d0dc2-199">兩數相除這個 RFC。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-199">This RFC divides two numbers.</span></span> <span data-ttu-id="d0dc2-200">在此範例中實作會使用**InboundActionCollection**篩選 Z_RFC_MKD_DIV 作業和下沒有收到訊息時：</span><span class="sxs-lookup"><span data-stu-id="d0dc2-200">The implementation in this example uses an **InboundActionCollection** to filter for the Z_RFC_MKD_DIV operation and does the following when a message is received:</span></span>  
  
-   <span data-ttu-id="d0dc2-201">如果除數為非零，它會將相除的結果寫入主控台的連線，並傳回至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-201">If the divisor is non-zero, it writes the result of the division to the console and returns it to the SAP system.</span></span>  
  
-   <span data-ttu-id="d0dc2-202">如果除數為零，它將產生的例外狀況訊息寫入主控台，並傳回錯誤給 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-202">If the divisor is zero, it writes the resulting exception message to the console and returns a fault to the SAP system.</span></span>  
  
-   <span data-ttu-id="d0dc2-203">如果 SAP 系統所傳送的任何其他作業，它會將訊息寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-203">If any other operation is sent by the SAP system, it writes a message to the console.</span></span> <span data-ttu-id="d0dc2-204">在此情況下，配接器本身會傳回錯誤給 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d0dc2-204">In this case, the adapter itself returns a fault to the SAP system.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.Runtime.Serialization;  
using System.Xml;  
using System.IO;  
  
// Add WCF, Adapter LOB SDK, and SAP Adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Add this namespace to use Channel Model   
using System.ServiceModel.Channels;  
  
// Include this namespace for Adapter LOB SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This sample demonstrates using the adapter as an rfc server over a channel.  
// The sample implements an RFC, Z_RFC_MKD_DIV that divides two numbers and returns the result  
// 1)  A SAPBinding instance is created and configured (AcceptCredentialsInUri is set true)  
// 2)  A binding parameter collection is created with an InboundAction collection that specifies  
//     target RFC (Z_RFC_MKD_DIV) so that only messages with this action will be received by the  
//     listener (and channel).  
// 3)  An <IReplyChannel> listener is created from the binding and binding parameter collection  
// 4)  A channel is created and opened to receive a request  
// 6)  When Z_RFC_MKD_DIV is received the two parameters are divided and the parameters and result  
//     are written to the console, then the result is returned to the adapter by using a template  
//     message.  
// 7)  If a divide by 0 occurs the exception message is written to the console and a  
//     fault is returned to the SAP system  
// 8)  If any other operation is received an error message is written to the console and the adapter  
///    returns a fault to the SAP system  
// 9)  IMPORTANT you must close the channel and listener to deregister them from the SAP Program ID.  
namespace SapRfcServerCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Variables to hold the listener and channel  
            IChannelListener<IReplyChannel> listener = null;  
            IReplyChannel channel = null;  
  
            Console.WriteLine("Sample started");  
            Console.WriteLine("Initializing and creating channel listener -- please wait");  
            try  
            {  
  
                // The connection Uri must specify listener parameters (or an R-type destination in saprfc.ini)  
                // and also credentials.  
                Uri listeneraddress =  
                    new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
  
                // Create a binding -- set AcceptCredentialsInUri true  
                SAPBinding binding = new SAPBinding();  
                binding.AcceptCredentialsInUri = true;  
  
                // Create a binding parameter collection with a list of SOAP actions to listen on  
                // in this case: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV  
                // This ensures that only these actions are received on the channel.  
                InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
                actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_DIV");  
                BindingParameterCollection bpcol = new BindingParameterCollection();  
                bpcol.Add(actions);  
  
                // Pass the Uri and the binding parameter collection (to specify the Z_RFC_MKD_DIV action)  
                listener = binding.BuildChannelListener<IReplyChannel>(listeneraddress, bpcol);  
  
                Console.WriteLine("Opening listener");  
                // Open the listener  
                listener.Open();  
  
                // Get an IReplyChannel  
                channel = listener.AcceptChannel();  
  
                Console.WriteLine("Opening channel");  
                // Open the channel  
                channel.Open();  
  
                Console.WriteLine("\nReady to receive Z_RFC_MKD_DIV RFC");  
  
                try  
                {  
                    // Get the message from the channel  
                    RequestContext rc = channel.ReceiveRequest();  
  
                    // Get the request message sent by SAP  
                    Message reqMessage = rc.RequestMessage;  
  
                    // get the message body  
                    XmlReader reader = reqMessage.GetReaderAtBodyContents();  
  
                    reader.ReadStartElement("Z_RFC_MKD_DIV");  
                    reader.ReadElementString("DEST");  
                    int x_in = int.Parse(reader.ReadElementString("X"));  
                    int y_in = int.Parse(reader.ReadElementString("Y"));  
                    reader.ReadEndElement();  
  
                    Console.WriteLine("\nRfc Received");  
                    Console.WriteLine("X =\t\t" + x_in);  
                    Console.WriteLine("Y =\t\t" + y_in);  
  
                    Message messageOut = null;  
  
                    try   
                    {  
                        int result_out = x_in/y_in;  
  
                        Console.WriteLine("RESULT =\t" + result_out.ToString());  
  
                        string out_xml = "<Z_RFC_MKD_DIVResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"><RESULT>" + result_out + "</RESULT></Z_RFC_MKD_DIVResponse>";  
                        StringReader sr = new StringReader(out_xml);  
                        reader = XmlReader.Create(sr);  
  
                        // create a response message  
                        // be sure to specify the response action  
                        messageOut = Message.CreateMessage(MessageVersion.Default, reqMessage.Headers.Action + "/response", reader);  
  
                    }  
                    catch (DivideByZeroException ex)  
                    {  
                        Console.WriteLine();  
                        Console.WriteLine(ex.Message + " Returning fault to SAP");  
  
                        // Create a message that contains a fault  
                        // The fault code and message action can be any value  
  
                        messageOut = Message.CreateMessage(MessageVersion.Default, new FaultCode("Fault"), ex.Message, string.Empty);  
                    }  
  
                    // Send the reply  
                    rc.Reply(messageOut);  
  
                    // Close the request context  
                    rc.Close();  
  
                }  
                catch (AdapterException aex)  
                {  
                    // Will get here if the message received was not in the InboundActionCollection  
                    Console.WriteLine();  
                    Console.WriteLine(aex.Message);  
                }  
  
                // Wait for a key to exit  
                Console.WriteLine("\nHit <RETURN> to end");  
                Console.ReadLine();  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the SAP system");  
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
                // IMPORTANT: close the channel and listener to stop listening on the Program ID  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0dc2-205">請參閱</span><span class="sxs-lookup"><span data-stu-id="d0dc2-205">See Also</span></span>  
[<span data-ttu-id="d0dc2-206">使用 WCF 通道模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="d0dc2-206">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)
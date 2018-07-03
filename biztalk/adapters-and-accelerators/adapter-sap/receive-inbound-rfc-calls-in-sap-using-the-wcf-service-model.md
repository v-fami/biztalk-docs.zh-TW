---
title: 使用 WCF 服務模型的 sap 接收輸入的 RFC 呼叫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving inbound RFC calls
- RFC calls, receiving inbound using the WCF service model
ms.assetid: 064d70d7-1603-467f-9aba-ecab78a567ff
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9650567f9f2072662af7f75d735a5a647de6d10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014183"
---
# <a name="receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model"></a><span data-ttu-id="d8b5f-102">使用 WCF 服務模型的 sap 接收輸入的 RFC 呼叫</span><span class="sxs-lookup"><span data-stu-id="d8b5f-102">Receive Inbound RFC Calls in SAP using the WCF Service Model</span></span>
<span data-ttu-id="d8b5f-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]可以做為 RFC 伺服器接收叫用的 SAP 系統的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] can act as an RFC server to receive RFCs invoked by a SAP system.</span></span>  
  
 <span data-ttu-id="d8b5f-104">若要接收輸入的 Rfc WCF 服務模型中，您必須：</span><span class="sxs-lookup"><span data-stu-id="d8b5f-104">To receive the inbound RFCs in the WCF service model, you must:</span></span>  
  
- <span data-ttu-id="d8b5f-105">確定 SAP 系統上存在的 RFC 目的地。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-105">Ensure that an RFC destination exists on the SAP system.</span></span>  
  
- <span data-ttu-id="d8b5f-106">請確定 RFC 定義於 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-106">Ensure that the RFC is defined on the SAP system.</span></span>  
  
- <span data-ttu-id="d8b5f-107">RFC 作業從配接器所公開的中繼資料產生 WCF 服務合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-107">Generate a WCF service contract (interface) for the RFC operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="d8b5f-108">若要這樣做，您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-108">To do this, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe).</span></span>  
  
- <span data-ttu-id="d8b5f-109">實作此介面的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-109">Implement a WCF service from this interface.</span></span> <span data-ttu-id="d8b5f-110">WCF 服務的方法包含處理 RFC，並將回應傳回給配接器所需的邏輯 (因此 SAP 系統)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-110">The methods of the WCF service contain the logic necessary to process the RFC and return a response to the adapter (and hence the SAP system).</span></span>  
  
- <span data-ttu-id="d8b5f-111">裝載此 WCF 服務，使用服務主機 (**System.ServiceModel.ServiceHost**)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-111">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
  <span data-ttu-id="d8b5f-112">下列各節會說明如何使用從 SAP 系統接收 Rfc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-112">The following sections show you how to receive RFCs from the SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="how-to-set-up-the-sap-system-to-send-an-rfc-to-the-sap-adapter"></a><span data-ttu-id="d8b5f-113">如何設定 SAP 系統傳送 RFC，SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="d8b5f-113">How to Set up the SAP System to Send an RFC to the SAP Adapter</span></span>  
 <span data-ttu-id="d8b5f-114">您可以從 SAP 系統傳送 RFC 之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須確定下列條件成立於 SAP 系統：</span><span class="sxs-lookup"><span data-stu-id="d8b5f-114">Before you can send an RFC from the SAP system to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], you must ensure that the following are true on the SAP system:</span></span>  
  
- <span data-ttu-id="d8b5f-115">RFC 目的地[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]必須存在。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-115">An RFC destination for the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] must exist.</span></span> <span data-ttu-id="d8b5f-116">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]註冊其本身與 RFC 目的地以接收來自 SAP 系統的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-116">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] registers itself with an RFC destination to receive RFCs from the SAP system.</span></span> <span data-ttu-id="d8b5f-117">您提供參數，在 SAP 連接 URI，例如 SAP 閘道器主機、 SAP 閘道服務，以及配接器用來向 SAP 程式 ID。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-117">You supply parameters in the SAP connection URI such as the SAP Gateway Host, the SAP Gateway Service, and the SAP Program ID that the adapter uses to register itself.</span></span> <span data-ttu-id="d8b5f-118">如需有關如何設定 SAP RFC 目的地的資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP 系統的 RFC](creating-an-rfc-in-an-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-118">For information about how to setup an RFC destination on SAP, see [Create an RFC, RFC destination, and send an RFC from SAP system](creating-an-rfc-in-an-sap-system.md).</span></span>  
  
- <span data-ttu-id="d8b5f-119">RFC 必須定義於 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-119">The RFC must be defined on the SAP system.</span></span> <span data-ttu-id="d8b5f-120">您必須建立定義於 SAP 系統的 RFC 函式模組。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-120">You must create a function module that defines the RFC on the SAP system.</span></span> <span data-ttu-id="d8b5f-121">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] SAP 系統上使用 RFC 定義，來擷取 RFC （兩者都在設計階段和執行階段） 的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-121">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the RFC definition on the SAP system to retrieve metadata about the RFC (both at design time and at run time).</span></span> <span data-ttu-id="d8b5f-122">如需詳細資訊，請參閱[SAP 系統中建立的 RFC](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-122">For more information see [Creating an RFC in an SAP System](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md).</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="d8b5f-123">您必須定義 RFC，SAP 系統中;不過您會在您的配接器用戶端程式碼中實作 RFC。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-123">You must define the RFC on the SAP system; however you implement the RFC in your adapter client code.</span></span> <span data-ttu-id="d8b5f-124">RFC 必須定義於 SAP 系統，使配接器可以擷取 RFC 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-124">The RFC must be defined on the SAP system so that the adapter can retrieve metadata for the RFC.</span></span>  
  
  <span data-ttu-id="d8b5f-125">以下是來源上的程式碼會加入兩個整數並傳回其結果的 RFC 的 SAP 系統的範例。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-125">The following is an example of the source code on the SAP system for an RFC that adds two integers and returns their result.</span></span> <span data-ttu-id="d8b5f-126">程式碼會透過指定的目的，只是呼叫 RFC。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-126">The code merely calls the RFC through a specified destination.</span></span> <span data-ttu-id="d8b5f-127">函式的實作由[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-127">The implementation of the function is done by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] client code.</span></span>  
  
```  
FUNCTION Z_RFC_SAMPLE_ADD.  
*"---------------------------------------------------------------------*"*"Local interface:  
*"  IMPORTING  
*"     VALUE(X) TYPE  INT4  
*"     VALUE(Y) TYPE  INT4  
*"     VALUE(DEST) TYPE  CHAR20 DEFAULT 'SAPADAPTER'  
*"  EXPORTING  
*"     VALUE(RESULT) TYPE  INT4  
*"---------------------------------------------------------------------CALL FUNCTION 'Z_RFC_MKD_ADD' DESTINATION DEST  
  EXPORTING X = X  
            Y = Y  
  IMPORTING RESULT = RESULT.  
  
ENDFUNCTION.  
```  
  
## <a name="the-wcf-service-contract-for-an-rfc"></a><span data-ttu-id="d8b5f-128">WCF 服務合約，如 RFC</span><span class="sxs-lookup"><span data-stu-id="d8b5f-128">The WCF Service Contract for an RFC</span></span>  
 <span data-ttu-id="d8b5f-129">您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 產生的 WCF 服務合約，如您願意收到來自 SAP 系統的 Rfc。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-129">You use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to generate a WCF service contract for the RFCs that you want to receive from the SAP system.</span></span> <span data-ttu-id="d8b5f-130">下列各節顯示的 managed 程式碼類別和 Z_RFC_MKD_ADD 作業產生的介面。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-130">The following sections show the managed code classes and interfaces generated for the Z_RFC_MKD_ADD operation.</span></span>  
  
### <a name="the-rfc-interface-wcf-service-contract"></a><span data-ttu-id="d8b5f-131">Rfc 介面 （WCF 服務合約）</span><span class="sxs-lookup"><span data-stu-id="d8b5f-131">The Rfc Interface (WCF service contract)</span></span>  
 <span data-ttu-id="d8b5f-132">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現所有 RFC 作業的單一服務合約，而 「 Rfc"。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-132">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces all RFC operations under a single service contract, "Rfc".</span></span> <span data-ttu-id="d8b5f-133">這表示單一介面， **Rfc**，系統會為所有您想要接收的 RFC 作業。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-133">This means that a single interface, **Rfc**, is created for all of the RFC operations that you want to receive.</span></span> <span data-ttu-id="d8b5f-134">RFC 作業的每一個目標被以這個介面的方法。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-134">Each target RFC operation is represented as a method of this interface.</span></span> <span data-ttu-id="d8b5f-135">每個方法會採用單一參數，代表作業的要求訊息的訊息合約，並且傳回一個物件，表示作業的回應訊息的訊息合約。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-135">Each method takes a single parameter, which represents the message contract for the request message of the operation, and returns an object, which represents the message contract of the response message of the operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/", ConfigurationName="Rfc")]  
public interface Rfc {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD/response")]  
    Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
}  
  
```  
  
### <a name="the-request-and-response-messages"></a><span data-ttu-id="d8b5f-136">要求和回應訊息</span><span class="sxs-lookup"><span data-stu-id="d8b5f-136">The Request and Response Messages</span></span>  
 <span data-ttu-id="d8b5f-137">每個 RFC 作業會使用參數來表示要求訊息，並傳回物件，表示回應訊息。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-137">Each RFC operation takes a parameter that represents the request message and returns an object that represents the response message.</span></span> <span data-ttu-id="d8b5f-138">要求訊息的屬性包含的匯入和 （輸入） 變更參數的 RFC。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-138">The properties of the request message contain the IMPORT and (input) CHANGING parameters of the RFC.</span></span> <span data-ttu-id="d8b5f-139">回應訊息的屬性會包含匯出，且 （輸出） 作業的變更參數。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-139">The properties of the response message contain the EXPORT and (output) CHANGING parameters for the operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", IsWrapped=true)]  
public partial class Z_RFC_MKD_ADDRequest {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=0)]  
    public string DEST;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=1)]  
    public System.Nullable<int> X;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=2)]  
    public System.Nullable<int> Y;  
  
    public Z_RFC_MKD_ADDRequest() {  
    }  
  
    public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y) {  
        this.DEST = DEST;  
        this.X = X;  
        this.Y = Y;  
    }  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADDResponse", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", IsWrapped=true)]  
public partial class Z_RFC_MKD_ADDResponse {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=0)]  
    public int RESULT;  
  
    public Z_RFC_MKD_ADDResponse() {  
    }  
  
    public Z_RFC_MKD_ADDResponse(int RESULT) {  
        this.RESULT = RESULT;  
    }  
}  
```  
  
### <a name="the-generated-wcf-service"></a><span data-ttu-id="d8b5f-140">產生的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="d8b5f-140">The Generated WCF Service</span></span>  
 <span data-ttu-id="d8b5f-141">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生實作 WCF 服務合約的 WCF 服務 (**Rfc**)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-141">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a WCF service that implements the WCF service contract (**Rfc**).</span></span> <span data-ttu-id="d8b5f-142">這個類別的方法被虛設常式。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-142">The methods of this class are stubbed.</span></span> <span data-ttu-id="d8b5f-143">這個類別會產生個別的檔案中。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-143">This class is generated in a separate file.</span></span> <span data-ttu-id="d8b5f-144">您可以直接在這個類別的方法來實作您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-144">You can implement your code directly in the methods of this class.</span></span>  
  
```  
namespace SAPBindingNamespace {  
  
    public class SAPBindingService : Rfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        public virtual Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="how-to-create-an-rfc-server-application"></a><span data-ttu-id="d8b5f-145">如何建立 RFC 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="d8b5f-145">How to Create an RFC Server Application</span></span>  
 <span data-ttu-id="d8b5f-146">若要使用 WCF 服務模型，從 SAP 系統接收 Rfc，您可以依照中的步驟[與 SAP 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-146">To receive RFCs from the SAP system by using the WCF service model, you can follow the steps in [Overview of the WCF Service Model with the SAP Adapter](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md).</span></span> <span data-ttu-id="d8b5f-147">請務必指定服務合約 'Rfc'，當您將新增服務端點 （建立和實作的 WCF 服務的程序的步驟 6）。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-147">Be sure to specify 'Rfc' for the service contract when you add the service endpoint (step 6 of the procedure for creating and implementing a WCF service).</span></span>  
  
 <span data-ttu-id="d8b5f-148">下列程式碼示範如何使用 Z_RFC_MKD_RFC 接收從 SAP 系統的完整範例[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-148">The following code shows a complete example of how to receive the Z_RFC_MKD_RFC from an SAP system by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="d8b5f-149">這個 RFC 採用兩個整數參數，並將結果傳回至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="d8b5f-149">This RFC takes two integer parameters and returns the result to the SAP system.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for the WCF LOB Adapter SDK and SAP adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace SapRfcServerSM  
{  
    // Implement a WCF service callback class by sub-classing the generated service callback class (SAPBindingService).  
    // You must annotate this class with the InstanceContextMode.Single ServiceBehavior  
    // If you implement your code in SAPBindingService.cs be sure to annotate the SAPBindingService class  
    // The callback method should return a Z_RFC_MKD_ADDResponse to indicate successful processing  
    // or throw an exception to indicate an error.  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
    class RfcServerClass : SAPBindingNamespace.SAPBindingService  
    {  
  
        public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
        {  
            // If either parameter is null, throw an exception   
            if (request.X == null || request.Y == null)  
                throw new System.ArgumentNullException();  
  
            int result = (int) (request.X + request.Y);  
  
            Console.WriteLine("\nRfc Received");  
            Console.WriteLine("X =\t\t" + request.X.ToString());  
            Console.WriteLine("Y =\t\t" + request.Y.ToString());  
            Console.WriteLine("Result =\t" + result);  
            Console.WriteLine("\nHit <RETURN> to end");  
  
            return new Z_RFC_MKD_ADDResponse(result);  
        }  
  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Listener connection for the service URI -- the connection URI must contain credentials  
            Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/ADAPSAP47/00?ListenerGwServ=SAPGW00&ListenerGwHost=ADAPSAP47&ListenerProgramId=ADDER");  
  
            // The baseUri cannot contain userinfoparams or query_string parameters  
            Uri[] baseUri = new Uri[] { new Uri("sap://a/ADAPSAP47/00") };  
  
            Console.WriteLine("RFC server sample started");  
  
            // create service instance  
            RfcServerClass rfcServerInstance = new RfcServerClass();  
  
            try  
            {  
                Console.WriteLine("Initializing service host -- please wait");  
                // Create and initialize a service host  
                using (ServiceHost srvHost = new ServiceHost(rfcServerInstance, baseUri))  
                {  
  
                    // Add service endpoint   
                    // Specify AcceptCredentalsInUri=true for the binding  
                    // NOTE: The contract for the service endpoint is "Rfc".  
                    //       This is the generated WCF service callback interface (see SAPBindingInterface.cs).  
                    SAPBinding binding = new SAPBinding();  
                    binding.AcceptCredentialsInUri = true;  
                    srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
                    srvHost.Open();  
  
                    Console.WriteLine("\nReady to receive Z_RFC_MKD_ADD RFC");  
                    Console.WriteLine("Hit <RETURN> to end");  
  
                    // Wait to receive request  
                    Console.ReadLine();  
                }  
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
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8b5f-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b5f-150">See Also</span></span>  
<span data-ttu-id="d8b5f-151">[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span><span class="sxs-lookup"><span data-stu-id="d8b5f-151">[Develop applications using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md) </span></span>  
 [<span data-ttu-id="d8b5f-152">RFC 作業的訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="d8b5f-152">Message Schemas for RFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)
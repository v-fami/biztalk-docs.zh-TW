---
title: 使用 WCF 服務模型的 SAP 中接收輸入 RFC 呼叫 |Microsoft 文件
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
ms.openlocfilehash: a415e3ab0ecbaab8778254d817241e5cafb61a92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22218454"
---
# <a name="receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model"></a>使用 WCF 服務模型的 SAP 中接收輸入 RFC 呼叫
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]可以做為 RFC 伺服器接收叫用的 SAP 系統的 Rfc。  
  
 若要接收傳入的 Rfc WCF 服務模型中，您必須：  
  
-   請確定 RFC 目的地存在於 SAP 系統。  
  
-   確定 RFC 定義 SAP 系統上。  
  
-   RFC 作業從配接器所公開的中繼資料產生 WCF 服務合約 （介面）。 若要這樣做，您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe)。  
  
-   實作這個介面從 WCF 服務。 WCF 服務的方法包含處理 RFC，並將回應傳回至配接器所需的邏輯 (因此 SAP 系統)。  
  
-   裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。  
  
 下列章節將示範如何使用從 SAP 系統接收 Rfc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="how-to-set-up-the-sap-system-to-send-an-rfc-to-the-sap-adapter"></a>如何設定 SAP 系統傳送 RFC，SAP 配接器  
 您可以從 SAP 系統傳送 RFC 之前[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]，您必須確定下列條件成立 SAP 系統上：  
  
-   RFC 目的地[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]必須存在。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]註冊其本身與 RFC 目的地以接收來自 SAP 系統的 Rfc。 您提供的 SAP 連線例如 SAP 閘道器主機、 SAP 閘道器服務，以及配接器用來向 SAP 程式 ID URI 中的參數。 如需如何設定 SAP RFC 目的地資訊，請參閱[建立 RFC、 RFC 目的地並傳送從 SAP 系統的 RFC](creating-an-rfc-in-an-sap-system.md)。  
  
-   必須定義 RFC，SAP 系統上。 您必須建立定義 RFC，SAP 系統的函式模組。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]使用 RFC 定義 SAP 系統上擷取 RFC （兩者都在設計階段和執行階段） 有關的中繼資料。 如需詳細資訊，請參閱[SAP 系統中建立 RFC](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md)。  
  
    > [!NOTE]
    >  您必須定義 RFC，SAP 系統。不過您會在配接器的用戶端程式碼中實作 RFC。 RFC 必須定義在 SAP 系統上，讓配接器可以擷取 RFC 的中繼資料。  
  
 以下是原始程式碼的將兩個整數並傳回其結果的 RFC 之 SAP 系統上的範例。 程式碼只會將 RFC 呼叫透過指定的目的地。 函式的實作由[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用戶端程式碼。  
  
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
  
## <a name="the-wcf-service-contract-for-an-rfc"></a>WCF 服務合約，如 RFC  
 您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生您想要從 SAP 系統接收的 Rfc 的 WCF 服務合約。 下列各節顯示的 managed 程式碼的類別和介面產生 Z_RFC_MKD_ADD 作業。  
  
### <a name="the-rfc-interface-wcf-service-contract"></a>Rfc 介面 （WCF 服務合約）  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現所有 RFC 作業的單一服務合約，"Rfc"。 這表示單一的介面， **Rfc**，建立所有您想要接收的 RFC 作業。 每個目標 RFC 作業被表示為這個介面的方法。 每個方法會接受單一參數，代表作業的要求訊息的訊息合約，並且傳回一個物件，表示作業的回應訊息的訊息合約。  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/", ConfigurationName="Rfc")]  
public interface Rfc {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD/response")]  
    Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
}  
  
```  
  
### <a name="the-request-and-response-messages"></a>要求和回應訊息  
 每個 RFC 作業會使用參數來表示要求訊息，並傳回物件，表示回應訊息。 要求訊息的屬性包含匯入和 RFC （輸入） 變更參數。 回應訊息的屬性包含匯出，而且 （輸出） 變更參數的作業。  
  
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
  
### <a name="the-generated-wcf-service"></a>產生的 WCF 服務  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生實作 WCF 服務合約的 WCF 服務 (**Rfc**)。 這個類別的方法是附加虛設常式。 這個類別會產生不同的檔案。 您可以直接在這個類別的方法來實作您的程式碼。  
  
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
  
## <a name="how-to-create-an-rfc-server-application"></a>如何建立 RFC 伺服器應用程式  
 若要使用 WCF 服務模型，從 SAP 系統接收 Rfc，您可以依照中的步驟[與 SAP 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md)。 請務必指定服務合約 'Rfc'，當您將新增服務端點 （建立和實作 WCF 服務的程序的步驟 6）。  
  
 下列程式碼將示範如何使用 Z_RFC_MKD_RFC 接收從 SAP 系統的完整範例[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。 這個 RFC 接受兩個整數參數，並傳回結果至 SAP 系統。  
  
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
  
## <a name="see-also"></a>另請參閱  
[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)
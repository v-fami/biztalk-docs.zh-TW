---
title: "傳送 Idoc 至 SAP 使用 WCF 服務模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, sending IDOCs to SAP
- IDOCs, sending to SAP by using the WCF service model
ms.assetid: 84077234-b82b-4e88-b858-ce2cb1383fb4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d9d550887271e2ba54d858456347ea85825554e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="send-idocs-to-sap-using-the-wcf-service-model"></a>傳送 Idoc 至 SAP 使用 WCF 服務模型
就內部而言，[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]傳送 Idoc 至 SAP 系統，藉由叫用的兩個的下列 Rfc 的其中一個：  
  
-   第 3 版 Idoc 的 IDOC_INBOUND_ASYNCHRONOUS。  
  
-   第 2 版 Idoc 的 INBOUND_IDOC_PROCESS。  
  
 您可以傳送 IDOC 至配接器的適當 RFC （或 tRFC）; 叫用不過，您也可以傳送 Idoc 至配接器使用兩個下列作業：  
  
-   **SendIdoc** IDOC 根節點正下方會顯示。 SendIdoc 作業的字串 （弱型別） 資料以傳送 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
-   **傳送**會個別顯示每個 idoc。 傳送作業會為強型別資料傳送 IDOC [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
 這些作業，判斷 IDOC 資料傳送至配接器的方式，不如何傳送至 SAP 系統。 配接器一律會依使用適當的 tRFC 傳送 IDOC 至 SAP 系統。  
  
 因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]傳送 IDOC tRFC，為傳送及 SendIdoc 作業公開您用來確認 （認可） 的 IDOC GUID 參數。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]在內部對應此使用 SAP 交易識別碼 (TID) tRFC 與相關聯的 GUID。 您可以確認 IDOC 中有兩種：  
  
-   使用**AutoConfirmSentIdocs**繫結屬性。 如果這個繫結屬性設為**true**，配接器會自動確認用來傳送 IDOC tRFC。  
  
-   藉由叫用 RfcConfirmTransID。 您可以呼叫這項作業 IDOC 相關聯的 guid。  
  
 下列各節將說明如何傳送 Idoc 至 SAP 系統中，使用 SendIdoc 和傳送作業。 如需可協助您以 tRFC 傳送 IDOC 的詳細資訊，請參閱[使用 WCF 服務模型來叫用 sap tRFCs](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
  
### <a name="the-sendidoc-operation"></a>SendIdoc 作業  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現以字串格式傳送 IDOC 的單一作業 （和服務合約）。 服務合約的名稱是"Idoc"，而 WCF 用戶端類別是**IdocClient**。  
  
 您可以使用此用戶端，對 SAP 傳送任何 IDOC。 它包含單一方法**SendIdoc**，採用兩個參數：  
  
-   **idocData**是一個字串，包含 IDOC 資料  
  
-   **guid**是對應到 SAP TID 的 GUID。  
  
 下列程式碼顯示針對 SendIdoc 作業所產生 WCF 用戶端。  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocClient : System.ServiceModel.ClientBase<Idoc>, Idoc {  
  
    public void SendIdoc(string idocData, ref System.Nullable\<System.Guid\> guid) {…}  
}  
```  
  
### <a name="the-send-operation"></a>傳送作業  
 傳送作業會使用強型別資料，因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現每個 IDOC 的唯一的服務合約。 這個合約為基礎的 IDOC 類型、 版本、 版次號碼和 CIM 類型 （如果適當的話），就會產生介面 （和 WCF 用戶端類別） 的名稱。 例如 ORDERS03.v3.620 idoc，介面名稱為"IdocORDERS03V3R620"且 WCF 用戶端類別為**IdocORDERS03V3R620Client**。  
  
 您必須產生唯一的用戶端的各種不同類型的 IDOC。 此用戶端包含單一方法**傳送**，採用兩個參數：  
  
-   **idocData**是表示強型別 IDOC 資料的類別。  
  
-   **guid**是對應到 SAP TID 之 guid 的字串表示。  
  
 下列程式碼顯示針對提出 ORDERS03.v3.620 IDOC 的傳送作業所產生 WCF 用戶端。  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocORDERS03V3R620Client : System.ServiceModel.ClientBase<IdocORDERS03V3R620>, IdocORDERS03V3R620 {  
  
    ...  
  
    public void Send(ORDERS03 idocData, ref string guid) { ... }  
}  
```  
  
## <a name="how-to-create-an-application-to-send-idocs"></a>如何建立傳送 Idoc 的應用程式  
 若要傳送 IDOC 到 SAP 系統，執行下列步驟。  
  
#### <a name="to-send-an-idoc-to-an-sap-system"></a>若要傳送 IDOC 至 SAP 系統  
  
1.  產生 WCF 用戶端類別。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生 WCF 用戶端類別為目標想要使用的 Idoc。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[SAP 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。 如果您想要明確地確認 Idoc，請確定您會產生 WCF 用戶端 RfcConfirmTransID 作業。 作業可以找到下的下列節點：  
  
    -   SendIdoc 作業。 直接在 IDOC 節點下。  
  
    -   傳送作業。 底下的節點對應至目標 IDOC 類型、 版本和版次數目。  
  
    -   RfcConfirmTransID 作業。 直接在 TRFC 節點下。  
  
2.  建立在步驟 1 所產生的 WCF 用戶端類別的執行個體，並指定用戶端繫結。 指定用戶端繫結牽涉到指定的繫結和 WCF 用戶端會使用的端點位址。 您可以在程式碼中以命令方式或是宣告式組態。 如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。 下列程式碼初始化從組態 IdocClient （適用於傳送作業中），以及設定 SAP 系統的認證。  
  
    ```  
    SAPBinding binding = new SAPBinding();  
  
    // Set endpoint address  
    EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
    // Create client and set credentials  
    idocClient = new IdocClient(binding, endpointAddress);  
    idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
    idocClient.ClientCredentials.UserName.Password = "YourPassword";;  
    ```  
  
3.  如果您想要確認 tRFC 之後 SAP 系統上的介面卡傳送 IDOC，設定**AutoConfirmSentIdocs**內容繫結至**true**。 開啟 WCF 用戶端之前，您必須這麼做。  
  
    ```  
    // Set AutoConfirmSentIdocs property to true  
    binding.AutoConfirmSentIdocs = true;  
    ```  
  
4.  開啟 WCF 用戶端。  
  
    ```  
    idocClient.Open();  
    ```  
  
5.  叫用 WCF 用戶端在步驟 2 中建立可傳送 IDOC 至 SAP 系統上的適當方法。 您可以將傳遞的變數，其中包含的 GUID，或者設定為**null**如**guid**參數。 如果您未指定 GUID[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]產生作業的其中一種 (**guid**是**ref**參數)。 下列程式碼會從檔案讀取 IDOC （以字串格式），並使用 SendIdoc 作業以將它傳送至 SAP 系統。  
  
    ```  
    // Read IDOC into string variable  
    using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
    {  
    idocData = reader.ReadToEnd();  
    }  
  
    //Get a new GUID to pass to SendIdoc. You can also assign a null  
    //value to have the adapter generate a GUID.  
    adapterTxGuid = Guid.NewGuid();  
  
    //Invoke SendIdoc on the client to send the IDOC to the SAP system  
    idocClient.SendIdoc(idocData, ref adapterTxGuid);  
    ```  
  
6.  如果您未設定**AutoConfirmSentIdocs**內容繫結至**true** （在步驟 3），然後您必須確認 tRFC SAP 系統上的。 若要這樣做您必須叫用**RfcConfirmTransID**方法**TrfcClient** （不會顯示建立）。 指定在步驟 4 參數中傳回 GUID。  
  
    ```  
    trfcClient.RfcConfirmTransID(adapterTxGuid);  
    ```  
  
7.  關閉 WCF 用戶端 (和**TrfcClient**，如果使用) 完成時 （您完成後，傳送 Idoc） 使用它。  
  
    ```  
    idocClient.Close();   
    ```  
  
### <a name="example"></a>範例  
 下列範例會傳送 IDOC 到 SAP 系統使用 SendIdoc 方法。 IDOC 是從檔案讀取，ORDERS03.txt。 此檔案包含 ORDERS03。V3.620 IDOC 和隨附的範例。不過，SendIdoc 作業可以用來傳送任何 IDOC。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This example sends a flat IDOC to the SAP system by using the SendIdoc operation.  
namespace SapIdocStringClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // variable for the IDOC client  
            IdocClient idocClient = null;  
  
            Console.WriteLine("IDOC string client sample started");  
            try  
            {  
                // Variable for the GUID  
                System.Nullable<System.Guid> adapterTxGuid;  
                // string to hold the Idoc data  
                string idocData;  
                // string to hold the SAP transaction ID (TID)  
                string sapTxId;  
  
                // The client can be configured from app.config, but it is   
                // explicitly configured here for demonstration.  
                // set AutoConfirmSentIdocs property to true  
                SAPBinding binding = new SAPBinding();  
                binding.AutoConfirmSentIdocs = true;  
  
                // Set endpoint address  
                EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPServer/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
                // Create client and set credentials  
                idocClient = new IdocClient(binding, endpointAddress);  
                idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
                idocClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the client and send the Idoc  
                idocClient.Open();  
  
                // Read IDOC into string variable  
                using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
                {  
                    idocData = reader.ReadToEnd();  
                }  
  
                //Get a new GUID to pass to SendIdoc. You can also assign a null.  
                //value to have the adapter generate a GUID.  
                adapterTxGuid = Guid.NewGuid();  
  
                //Invoke SendIdoc on the client to send the IDOC to the SAP system.  
                idocClient.SendIdoc(idocData, ref adapterTxGuid);  
  
                // The AutoConfirmSentIdocs binding property is set to true, so there is no need to  
                // confirm the IDOC. If this property is not set to true, you must call the   
                // RfcConfirmTransID method of a TrfcClient with adapterTxGuid to   
                // confirm the transaction on the SAP system.   
  
                // Get SAP tx id from GUID  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid((Guid) adapterTxGuid);  
  
                Console.WriteLine("IDOC sent");  
                Console.WriteLine("The SAP Transaction Id is : " + sapTxId);  
  
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
                // Close the IDOC client  
                if (idocClient != null)  
                {  
                    if (idocClient.State == CommunicationState.Opened)  
                        idocClient.Close();  
                    else  
                        idocClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>請參閱  
[使用 WCF 服務模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)
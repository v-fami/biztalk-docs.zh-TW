---
title: 叫用中使用 WCF 服務模型的 SAP Rfc |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invoking RFCs, using the WCF service model
- WCF service model, invoking RFCs
ms.assetid: 06a373e2-5d16-4480-81ec-611bd0b9749c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8a18e9ae4990ecd5e85c57fc86919f239d51cbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217518"
---
# <a name="invoke-rfcs-in-sap-using-the-wcf-service-model"></a>叫用中使用 WCF 服務模型的 SAP Rfc
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] SAP 系統 Rfc 會呈現為可以叫用用戶端程式的作業。 在 WCF 服務模型中，這些作業會為產生的 WCF 用戶端類別的方法叫用。 您可以使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別，其中包含您想要叫用程式碼中每個 RFC 的方法。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生封裝所使用的每個 RFC 的參數和資料類型的.NET 型別。 然後，您可以建立此 WCF 用戶端類別的執行個體，並呼叫其方法來叫用目標 Rfc。  
  
 下列章節將示範如何使用 SAP 系統上叫用 Rfc [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]呈現所有 RFC 作業的單一服務合約，"Rfc"。 這表示單一的 WCF 用戶端類別， **RfcClient**，建立所有您想要叫用的 RFC 作業。 RFC 的每一個目標被以這個類別的方法。 在每個方法：  
  
-   SAP 匯出參數當成**出**參數  
  
-   SAP 變更參數當成**ref**參數。  
  
-   複雜的 SAP 類型，例如結構顯示為.NET 類別有屬性對應至 SAP 類型的欄位。 這些類別會定義下列命名空間中： microsoft.lobservices.sap._2007._03.Types.Rfc。  
  
 下列程式碼顯示部分**RfcClient**類別並會 SD_RFC_CUSTOMER_GET SAP 系統叫用的方法。  
  
```  
 [System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class RfcClient : System.ServiceModel.ClientBase<Rfc>, Rfc {  
  
    ...  
  
    /// <summary>The metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="KUNNR">Customer number</param>  
    /// <param name="NAME1">Name of the customer</param>  
    /// <param name="CUSTOMER_T">Table of the selected customers</param>  
    /// <returns></returns>  
    public void SD_RFC_CUSTOMER_GET(string KUNNR, string NAME1, ref microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] CUSTOMER_T) {...}  
}  
```  
  
## <a name="how-to-create-an-rfc-client-application"></a>如何建立 RFC 用戶端應用程式  
 若要建立的 RFC 用戶端應用程式，執行下列步驟。  
  
#### <a name="to-create-an-rfc-client-application"></a>若要建立的 RFC 用戶端應用程式  
  
1.  產生**RfcClient**類別。 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來產生**RfcClient**為目標的 Rfc，您要使用的類別。 如需如何產生 WCF 用戶端的詳細資訊，請參閱[SAP 方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)。  
  
2.  建立的執行個體**RfcClient**類別中產生的步驟 1，並指定用戶端繫結。 指定用戶端繫結牽涉到指定的繫結和端點位址， **RfcClient**將會使用。 您可以在程式碼中以命令方式或是宣告式組態。 如需如何指定用戶端繫結的詳細資訊，請參閱[SAP 系統設定用戶端繫結](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)。 下列程式碼會初始化**RfcClient**來自組態和集合 SAP 系統的認證。  
  
    ```  
    RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  開啟 WCF 用戶端。  
  
    ```  
    rfcClient.Open();  
    ```  
  
4.  在上叫用方法**RfcClient**步驟在 SAP 系統上執行作業 2 中建立。 下列程式碼會叫用**SD_RFC_CUSTOMER_GET**方法**RfcClient** RFC，SAP 系統上的叫用。  
  
    ```  
    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
        new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
    ```  
  
5.  關閉 WCF 用戶端。  
  
    ```  
    rfcClient.Close();   
    ```  
  
### <a name="example"></a>範例  
 以下是完整的程式碼範例會叫用 SD_RFC_CUSTOMER_GET 傳回一份客戶名稱開頭為"AB"，然後的名稱和識別碼將每個客戶的寫入主控台。 這個範例會建立**RfcClient**內**使用**陳述式。 不需要明確地關閉**RfcClient**; 將會關閉時的執行路徑結束內容。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.SAP;  
  
namespace SapRfcClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                // Create client from configuration  
                using (RfcClient rfcClient = new RfcClient("SAPBinding_Rfc"))  
                {  
  
                    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
                    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                    // Open client  
                    rfcClient.Open();  
  
                    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers = new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
                    // Invoke SD_RFC_CUSTOMER_GET  
                    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
  
                    // Write the results to the console  
                    foreach (microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST customer in customers)  
                    {  
                        Console.WriteLine("Customer Name = " + customer.NAME1);  
                        Console.WriteLine("         Id   = " + customer.KUNNR);  
                        Console.WriteLine();  
                    }  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
                if (ex.InnerException != null)  
                    Console.WriteLine("Inner exception is :" + ex.InnerException);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
[開發應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [RFC 作業的訊息結構描述](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)
---
title: 叫用同時執行的程式中使用 WCF 服務模型的 Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e227c60f-f6fe-40bf-bf41-2784a4428ad0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81f181cfad40c31abc0d5b3517f0d7f8d9c32d7b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002351"
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model"></a>叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式
Oracle E-business Suite 會公開您可以執行特定作業在 Oracle 應用程式上的執行的並行處理程式。 每個 Oracle 應用程式有一組標準的並行程式 （可在所有作業，都是相同） 和 Oracle 應用程式專屬特定並行程式。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開所有的並行程式做為配接器用戶端可以叫用的作業。 如需配接器如何支援同時執行的程式的詳細資訊，請參閱[並行程式的相關作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。  
  
> [!NOTE]
>  並行程式不會公開其中繼資料、 Oracle E-business 配接器會公開這些並行程式的每個 100 的選擇性參數。 已成功叫用這些並行程式，使用者必須請參閱 Oracle E-business Suite 文件，找出需要值，並行處理程式的參數，且然後將其指定。 這類並行程式的範例**日誌匯入**(實際名稱： **GLLEZL**) 中**一般分類帳**應用程式。  
  
## <a name="about-the-examples-used-in-this-topic"></a>有關使用本主題中的範例  
 本主題中的範例會叫用**MS_SAMPLE_COPY_EMP_DATA**並行處理程式，後面接著**Get_Status**須知的第一個並行處理程式狀態的並行處理程式。 這些並行程式會從叫用**應用程式物件程式庫**應用程式。 **MS_SAMPLE_COPY_EMP_DATA**由執行指令碼提供範例。 如需有關範例的詳細資訊，請參閱 < [Oracle EBS 配接器的範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **ConcurrentProgram_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用同時執行的程式所產生的 WCF 用戶端名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會列在下表。  
  
|成品|WCF 用戶端名稱|  
|--------------|---------------------|  
|並行處理程式|ConcurrentPrograms_[APP_NAME]Client|  
  
 [APP_NAME>] = [Oracle E-business Suite 應用程式的實際名稱例如，尋找說明。  
  
### <a name="method-signature-for-invoking-concurrent-programs"></a>叫用同時執行的程式的方法簽章  
 下表顯示並行程式的方法簽章。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|並行處理程式|公用\<傳回型別\>< Concurrent_program_name > （參數 1，參數 2，...）|  
  
 例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**MS_SAMPLE_COPY_EMP_DATA**並**Get_Status**同時執行的程式。  
  
```  
public partial class ConcurrentPrograms_FNDClient : System.ServiceModel.ClientBase<ConcurrentPrograms_FND>, ConcurrentPrograms_FND {      
  
    public string MS_SAMPLE_COPY_EMP_DATA(schemas.microsoft.com.OracleEBS._2008._05.Options.SetOptions SetOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetPrintOptions SetPrintOptions,  
      schemas.microsoft.com.OracleEBS._2008._05.Options.SetRepeatOptions SetRepeatOptions,  
      string Description, string StartTime);  
  
    public bool GetStatusForConcurrentProgram(string RequestId, out string Phase, out string Status,  
      out string DevPhase, out string DevStatus, out string Message);  
}  
```  
  
 在此片段中， **ConcurrentPrograms_FNDClient**是 WCF 中類別的名稱所產生 OracleEBSBindingClient.cs [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 **MS_SAMPLE_COPY_EMP_DATA**是並行處理程式的叫用方法的名稱。 **GetStatusForConcurrentProgram**並行程式，以取得狀態的第一個並行程式的叫用方法的名稱。  
  
> [!NOTE]
>  **GetStatusForConcurrentProgram**是的實際名稱**Get_Status**並行處理程式。  
  
## <a name="creating-a-wcf-client-to-invoke-concurrent-programs"></a>建立 WCF 用戶端來叫用同時執行的程式  
 一組標準的 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需的動作牽涉到一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。 本節說明如何建立 WCF 用戶端來叫用**MS_SAMPLE_COPY_EMP_DATA**並**Get_Status**同時執行的程式。  
  
#### <a name="to-create-a-wcf-client"></a>若要建立的 WCF 用戶端  
  
1. Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2. 產生 WCF 用戶端類別，如**MS_SAMPLE_COPY_EMP_DATA**並**Get_Status**同時執行的程式。 如需有關如何產生 WCF 用戶端類別的詳細資訊，請參閱 <<c0> [ 產生 WCF 用戶端或 Oracle E-business Suite 解決方案成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
   > [!IMPORTANT]
   >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3. 在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。  
  
4. 開啟 Program.cs 檔案並新增下列命名空間：  
  
   -   `Microsoft.Adapters.OracleEBS`  
  
   -   `System.ServiceModel`  
  
5. 開啟 Program.cs 檔案，並建立用戶端，如下列程式碼片段中所述。  
  
   ```  
   OracleEBSBinding binding = new OracleEBSBinding();  
   EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
   ConcurrentPrograms_FNDClient client = new ConcurrentPrograms_FNDClient(binding, address);  
   ```  
  
    在此片段中， `ConcurrentPrograms_FNDClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 此檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
   > [!NOTE]
   >  在此片段中，您明確指定的繫結與端點位址在您的應用程式程式碼。 您也可以使用這些值，從應用程式組態檔 app.config，也產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需有關指定用戶端繫結的不同方式的詳細資訊，請參閱[設定用戶端 for Oracle E-business Suite 繫結](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  
  
6. 設定用戶端的認證。  
  
   ```  
   client.ClientCredentials.UserName.UserName = "myuser";  
   client.ClientCredentials.UserName.Password = "mypassword";  
   ```  
  
7. 因為您所叫用 Oracle E-business Suite 應用程式中的並行程式，您必須設定應用程式內容。 在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，並**OracleEBSResponsibilityName**繫結屬性。 如需有關應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
   ```  
   binding.OracleUserName = "myOracleEBSUserName";  
   binding.OraclePassword = "myOracleEBSPassword";  
   binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
   ```  
  
8. 下列程式碼片段中所述，請開啟用戶端：  
  
   ```  
   try  
   {  
      Console.WriteLine("Opening Client...");  
      client.Open();  
   }  
   catch (Exception ex)  
   {  
      Console.WriteLine("Exception: " + ex.Message);  
      throw;  
   }  
   ```  
  
9. 叫用**MS_SAMPLE_COPY_EMP_DATA**並**Get_Status**同時執行的程式。  
  
    ```  
    string RequestID;  
    bool Result;  
    string Phase;  
    string Status;  
    string DevPhase;  
    string DevStatus;  
    string Message;  
  
    try  
    {  
        Console.WriteLine("Invoking the MS_SAMPLE_COPY_EMP_DATA concurrent program");  
        RequestID = client.MS_SAMPLE_COPY_EMP_DATA(null, null, null, null, null);  
        Console.WriteLine("The request ID generated for the concurrent program is : " + RequestID);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nWaiting for 60 seconds for the concurrent program to be complete");  
        System.Threading.Thread.Sleep(60000);  
        Console.WriteLine("\nInvoking the Get_Status concurrent program");  
        Result = client.GetStatusForConcurrentProgram(RequestID, out Phase, out Status, out DevPhase, out DevStatus, out Message);  
        Console.WriteLine("\nResult is  : " + Result);  
        Console.WriteLine("Phase is     : " + Phase);  
        Console.WriteLine("Status is    : " + Status);  
        Console.WriteLine("DevPhase is  : " + DevPhase);  
        Console.WriteLine("DevStatus is : " + DevStatus);  
        Console.WriteLine("Message is   : " + Message);  
        Console.WriteLine("********************************************************");  
        Console.WriteLine("\nHit <RETURN> to end");  
        Console.ReadLine();  
    }  
    catch (Exception ex)  
    {  
        Console.WriteLine("Exception : " + ex);  
        throw;                 
    }  
    ```  
  
10. 下列程式碼片段中所述，請關閉該用戶端：  
  
    ```  
    client.Close();  
    ```  
  
11. 建置專案，然後執行它。 應用程式叫用**MS_SAMPLE_COPY_EMP_DATA**並傳回要求識別碼。 識別碼會傳遞至**Get_Status**並行處理程式，最後會提供狀態**MS_SAMPLE_COPY_EMP_DATA**資料行的程式。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
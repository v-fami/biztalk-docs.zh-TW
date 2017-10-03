---
title: "叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e227c60f-f6fe-40bf-bf41-2784a4428ad0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aed2b50eab9612e5a2a610047e41560e1dc24576
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model"></a>叫用 Oracle E-business Suite 使用 WCF 服務模型中的並行程式
Oracle E-business Suite 會公開您可以執行特定操作 Oracle 應用程式上的執行的並行程式。 每個 Oracle 應用程式有一組標準的並行程式 （也就是相同的所有作業） 和特定 Oracle 應用程式專屬的並行程式。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開所有的並行程式做為配接器用戶端可以叫用的作業。 如需配接器如何支援同時執行之程式的詳細資訊，請參閱[上同時執行之程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)。  
  
> [!NOTE]
>  Oracle E-business 配接器不會公開其中繼資料的並行程式，每個這些並行程式可 100 的選擇性參數。 順利叫用這些並行程式，使用者必須請參閱 Oracle E-business Suite 文件，找出需要值，並行處理程式的參數，然後將其指定。 並行程式的範例是**筆記本的匯入**(實際名稱： **GLLEZL**) 中**一般分類帳**應用程式。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例會叫用**MS_SAMPLE_COPY_EMP_DATA**並行程式，後面接著**Get_Status**並行程式知道第一個並行程式的狀態。 這些並行程式會從叫用**應用程式物件程式庫**應用程式。 **MS_SAMPLE_COPY_EMP_DATA**建立執行範例所提供的指令碼。 如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **ConcurrentProgram_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-wcf-client-class"></a>WCF 用戶端類別  
 叫用同時執行之程式所產生的 WCF 用戶端名稱[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]列於下表。  
  
|成品|WCF 用戶端名稱|  
|--------------|---------------------|  
|並行程式|ConcurrentPrograms_ [APP_NAME] 用戶端|  
  
 [APP_NAME] = Oracle E-business Suite 應用程式; 的實際名稱例如，尋找說明。  
  
### <a name="method-signature-for-invoking-concurrent-programs"></a>叫用同時執行之程式的方法簽章  
 下表顯示並行程式的方法簽章。  
  
|作業|方法簽章|  
|---------------|----------------------|  
|並行程式|公用\<傳回型別 >< Concurrent_program_name > （參數 1，參數 2，...）|  
  
 例如，下列程式碼顯示的方法簽章產生 WCF 用戶端類別**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。  
  
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
  
 在此程式碼片段， **ConcurrentPrograms_FNDClient**是 WCF 中的類別所產生的 OracleEBSBindingClient.cs 名稱[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 **MS_SAMPLE_COPY_EMP_DATA**並行程式的叫用方法的名稱。 **GetStatusForConcurrentProgram**並行程式來取得第一次的並行處理程式狀態的叫用方法的名稱。  
  
> [!NOTE]
>  **GetStatusForConcurrentProgram**的實際名稱**Get_Status**並行處理程式。  
  
## <a name="creating-a-wcf-client-to-invoke-concurrent-programs"></a>建立 WCF 用戶端來叫用同時執行的程式  
 Oracle E-business Suite 使用 WCF 用戶端上執行作業所需動作的泛型集合會包含一組工作中所述[Oracle E-business Suite 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)。 本章節描述如何建立 WCF 用戶端來叫用**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。  
  
#### <a name="to-create-a-wcf-client"></a>若要建立 WCF 用戶端  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  產生 WCF 用戶端類別**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。 如需產生 WCF 用戶端類別的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約，如 Oracle E-business Suite 方案成品](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)。  
  
    > [!IMPORTANT]
    >  在之前產生 WCF 用戶端類別，請確定您設定**EnableBizTalkCompatibilityMode**繫結屬性為 false。  
  
3.  在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`和`Microsoft.ServiceModel.Channels`。  
  
4.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  開啟 Program.cs 檔案並建立用戶端，如以下程式碼片段中所述。  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
    ConcurrentPrograms_FNDClient client = new ConcurrentPrograms_FNDClient(binding, address);  
    ```  
  
     在此程式碼片段， `ConcurrentPrograms_FNDClient` OracleEBSBindingClient.cs 中定義之 WCF 用戶端。 這個檔案由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。  
  
    > [!NOTE]
    >  在此片段中，您明確指定的繫結與端點位址的應用程式程式碼中。 您也可以使用這些值從應用程式組態檔 app.config，也是由產生[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。 如需以不同的方式指定用戶端繫結的詳細資訊，請參閱[for Oracle E-business Suite 繫結的用戶端設定](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)。  
  
6.  設定用戶端的認證。  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  因為您叫用 Oracle E-business Suite 應用程式中的並行程式，您必須設定應用程式內容。 在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  以下程式碼片段中所述，請開啟用戶端：  
  
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
  
9. 叫用**MS_SAMPLE_COPY_EMP_DATA**和**Get_Status**並行程式。  
  
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
  
10. 以下程式碼片段中所述，請關閉用戶端：  
  
    ```  
    client.Close();  
    ```  
  
11. 建置專案，然後執行它。 應用程式會叫用**MS_SAMPLE_COPY_EMP_DATA**並傳回要求的識別碼。 識別碼會傳遞至**Get_Status**並行程式，最後會提供狀態**MS_SAMPLE_COPY_EMP_DATA**資料行的程式。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
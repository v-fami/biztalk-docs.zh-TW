---
title: 執行 Oracle E-business Suite 使用 WCF 通道模型中的介面資料表上的 insert 作業 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a2e5ee3-552b-40a2-aaa6-5391347f1146
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 703b00adeb373fe66c4a96c324f13f9c3c5ec655
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216734"
---
# <a name="run-an-insert-operation-on-an-interface-table-in-oracle-e-business-suite-using-the-wcf-channel-model"></a>執行 Oracle E-business Suite 使用 WCF 通道模型中的介面資料表上的 insert 作業
[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]探索一組 Oracle E-business Suite 介面資料表的 Insert、 Select、 Update 和 Delete 作業。 藉由使用這些作業，您可以執行簡單的 Insert、 Select、 Update 和 Delete 陳述式以 Where 限定目標介面資料表上的子句。 本主題提供有關如何執行插入作業使用 WCF 通道模型的介面資料表上的指示。  
  
 如需有關配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。 如需如何在 Oracle E-business Suite 使用 WCF 通道模型上執行作業的詳細資訊，請參閱[Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)。  
  
## <a name="about-the-examples-used-in-this-topic"></a>關於本主題中使用的範例  
 本主題中的範例執行 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。 執行範例所提供的指令碼會建立資料表。 如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。 範例中， **InsertOperation**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。  
  
## <a name="the-insert-message"></a>插入訊息  
 若要執行使用 WCF 通道模型 Oracle E-business suite 作業，您必須使用特定作業的要求訊息。 要執行插入作業 MS_SAMPLE_EMPLOYEE 介面資料表上的要求訊息如下所示：  
  
```  
<Insert xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
  <RECORDSET>  
    <InsertRecord xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/TableViewRecord/APPS/MS_SAMPLE_EMPLOYEE">  
      <EMP_NO>10050</EMP_NO>  
      <NAME>John Smith</NAME>  
      <DESIGNATION>Manager</DESIGNATION>  
      <SALARY>500000</SALARY>  
      <JOIN_DATE>1999-05-31</JOIN_DATE>  
    </InsertRecord>  
  </RECORDSET>  
</Insert>  
```  
  
 此要求訊息會插入記錄，詳細資料如下：  
  
```  
Employee Number = 10050  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 您必須將訊息複製到檔案，例如 InsertRequest.xml。 此檔案用於在此範例中將要求訊息傳送至 Oracle E-business Suite 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需資料表作業的訊息結構描述的詳細資訊，請參閱[Insert、 Update、 Delete 和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)。  
  
## <a name="creating-a-wcf-channel-application"></a>建立 WCF 通道應用程式  
 本節提供有關如何建立 WCF 通道應用程式執行插入作業 MS_SAMPLE_EMPLOYEE 介面資料表上的指示。  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-table"></a>若要建立的 WCF 通道應用程式將記錄插入資料表  
  
1.  Visual Studio 中建立 Visual C# 專案。 本主題中，建立主控台應用程式。  
  
2.  在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。  
  
3.  開啟 Program.cs 檔案並加入下列命名空間：  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  建立繫結和端點。  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
  
    ```  
  
5.  因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。 在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。 如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  建立並開啟通道處理站。 此應用程式將要求訊息傳送給 Oracle E-business Suite，並接收回應，因此您必須實作 IRequestChannel 介面。  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
7.  建立並開啟通道。  
  
    ```  
    IRequestChannel channel;  
    try  
    {  
       channel = factory.CreateChannel();  
       channel.Open();  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception :" + ex.Message);  
       throw;  
    }  
    ```  
  
8.  建立並傳送要求訊息。  
  
    ```  
    XmlReader readerIn;  
    try  
    {  
       readerIn = XmlReader.Create("InsertRequest.xml");  
       Console.WriteLine("Reader created");  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Message messageIn;  
    Message messageOut;  
    try  
    {  
       messageIn = Message.CreateMessage(MessageVersion.Default, "InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE", readerIn);  
       messageOut = channel.Request(messageIn);  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    ```  
  
     在建立要求訊息時，您必須指定表示配接器介面在資料表執行的動作的訊息動作。 若要執行插入作業 MS_SAMPLE_EMPLOYEE 資料表上的，為訊息動作`InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`。 如需如何判斷在資料表上的各種動作的訊息動作資訊，請參閱[Insert、 Update、 Delete 和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)。  
  
9. 取得回應訊息。  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
10. 關閉訊息、 通道和通道處理站。  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
11. 建置專案。 建置專案之後, 您必須複製的要求訊息，InsertRequest.xml，在您的專案可執行檔相同的位置。 一般而言，這個位置是專案目錄底下的 \bin\Debug\。  
  
12. 執行應用程式。 回應訊息，Response.xml，會儲存您的應用程式中指定的位置。 回應訊息包含數字或插入的記錄，如下所示：  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
      <InsertResult>1</InsertResult>  
    </InsertResponse>  
    ```  
  
     值"1"代表單一資料錄插入 MS_SAMPLE_EMPLOYEE 資料表。  
  
## <a name="see-also"></a>另請參閱  
 [開發 Oracle E-business Suite 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
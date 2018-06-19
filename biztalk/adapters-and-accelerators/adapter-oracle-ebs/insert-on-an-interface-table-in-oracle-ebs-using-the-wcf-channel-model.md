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
# <a name="run-an-insert-operation-on-an-interface-table-in-oracle-e-business-suite-using-the-wcf-channel-model"></a><span data-ttu-id="724db-102">執行 Oracle E-business Suite 使用 WCF 通道模型中的介面資料表上的 insert 作業</span><span class="sxs-lookup"><span data-stu-id="724db-102">Run an insert operation on an interface table in Oracle E-Business Suite using the WCF channel model</span></span>
<span data-ttu-id="724db-103">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]探索一組 Oracle E-business Suite 介面資料表的 Insert、 Select、 Update 和 Delete 作業。</span><span class="sxs-lookup"><span data-stu-id="724db-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] discovers a set of Insert, Select, Update, and Delete operations on Oracle E-Business Suite interface tables.</span></span> <span data-ttu-id="724db-104">藉由使用這些作業，您可以執行簡單的 Insert、 Select、 Update 和 Delete 陳述式以 Where 限定目標介面資料表上的子句。</span><span class="sxs-lookup"><span data-stu-id="724db-104">By using these operations, you can perform simple Insert, Select, Update, and Delete statements qualified by a Where clause on a target interface table.</span></span> <span data-ttu-id="724db-105">本主題提供有關如何執行插入作業使用 WCF 通道模型的介面資料表上的指示。</span><span class="sxs-lookup"><span data-stu-id="724db-105">This topic provides instructions on how to perform an Insert operation on an interface table using the WCF channel model.</span></span>  
  
 <span data-ttu-id="724db-106">如需有關配接器如何支援這些作業的詳細資訊，請參閱[介面資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)。</span><span class="sxs-lookup"><span data-stu-id="724db-106">For more information on how the adapter supports these operations, see [Operations on Interface Tables and Interface Views](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md).</span></span> <span data-ttu-id="724db-107">如需如何在 Oracle E-business Suite 使用 WCF 通道模型上執行作業的詳細資訊，請參閱[Oracle E-business Suite 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="724db-107">For more information about how to perform operations on Oracle E-Business Suite using the WCF Channel model, see [Overview of the WCF channel model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="724db-108">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="724db-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="724db-109">本主題中的範例執行 MS_SAMPLE_EMPLOYEE 介面資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="724db-109">The example in this topic performs operations on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="724db-110">執行範例所提供的指令碼會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="724db-110">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="724db-111">如需有關範例的詳細資訊，請參閱[Oracle EBS 配接器範例](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="724db-111">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="724db-112">範例中， **InsertOperation**，根據本主題中，也會提供與[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="724db-112">A sample, **InsertOperation**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-insert-message"></a><span data-ttu-id="724db-113">插入訊息</span><span class="sxs-lookup"><span data-stu-id="724db-113">The Insert Message</span></span>  
 <span data-ttu-id="724db-114">若要執行使用 WCF 通道模型 Oracle E-business suite 作業，您必須使用特定作業的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="724db-114">To perform operations on the Oracle E-Business Suite using the WCF channel model, you must have the request message specific to the operation.</span></span> <span data-ttu-id="724db-115">要執行插入作業 MS_SAMPLE_EMPLOYEE 介面資料表上的要求訊息如下所示：</span><span class="sxs-lookup"><span data-stu-id="724db-115">The request message to perform an Insert operation on the MS_SAMPLE_EMPLOYEE interface table resembles the following:</span></span>  
  
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
  
 <span data-ttu-id="724db-116">此要求訊息會插入記錄，詳細資料如下：</span><span class="sxs-lookup"><span data-stu-id="724db-116">This request message inserts a record with following details:</span></span>  
  
```  
Employee Number = 10050  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 <span data-ttu-id="724db-117">您必須將訊息複製到檔案，例如 InsertRequest.xml。</span><span class="sxs-lookup"><span data-stu-id="724db-117">You must copy the message to a file, e.g. InsertRequest.xml.</span></span> <span data-ttu-id="724db-118">此檔案用於在此範例中將要求訊息傳送至 Oracle E-business Suite 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="724db-118">This file is used in this example to send the request message to Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="724db-119">如需資料表作業的訊息結構描述的詳細資訊，請參閱[Insert、 Update、 Delete 和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="724db-119">For more information about the message schema for operations on table, see [Message Schemas for Insert, Update, Delete, and Select Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).</span></span>  
  
## <a name="creating-a-wcf-channel-application"></a><span data-ttu-id="724db-120">建立 WCF 通道應用程式</span><span class="sxs-lookup"><span data-stu-id="724db-120">Creating a WCF Channel Application</span></span>  
 <span data-ttu-id="724db-121">本節提供有關如何建立 WCF 通道應用程式執行插入作業 MS_SAMPLE_EMPLOYEE 介面資料表上的指示。</span><span class="sxs-lookup"><span data-stu-id="724db-121">This section provides instructions on how to create a WCF channel application to perform an Insert operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-table"></a><span data-ttu-id="724db-122">若要建立的 WCF 通道應用程式將記錄插入資料表</span><span class="sxs-lookup"><span data-stu-id="724db-122">To create a WCF channel application for inserting records into the table</span></span>  
  
1.  <span data-ttu-id="724db-123">Visual Studio 中建立 Visual C# 專案。</span><span class="sxs-lookup"><span data-stu-id="724db-123">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="724db-124">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="724db-124">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="724db-125">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleEBS`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。</span><span class="sxs-lookup"><span data-stu-id="724db-125">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="724db-126">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="724db-126">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="724db-127">建立繫結和端點。</span><span class="sxs-lookup"><span data-stu-id="724db-127">Create the binding and endpoint.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs_instance_name");  
  
    ```  
  
5.  <span data-ttu-id="724db-128">因為您正在執行的介面資料表上的作業，您必須設定應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="724db-128">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="724db-129">在此範例中，若要設定應用程式內容中，您指定**OracleUserName**， **OraclePassword**，和**OracleEBSResponsibilityName**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="724db-129">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="724db-130">如需應用程式內容的詳細資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。</span><span class="sxs-lookup"><span data-stu-id="724db-130">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  <span data-ttu-id="724db-131">建立並開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="724db-131">Create and open the channel factory.</span></span> <span data-ttu-id="724db-132">此應用程式將要求訊息傳送給 Oracle E-business Suite，並接收回應，因此您必須實作 IRequestChannel 介面。</span><span class="sxs-lookup"><span data-stu-id="724db-132">This application sends request message to Oracle E-Business Suite and receives a response, hence you must implement the IRequestChannel interface.</span></span>  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
7.  <span data-ttu-id="724db-133">建立並開啟通道。</span><span class="sxs-lookup"><span data-stu-id="724db-133">Create and open the channel.</span></span>  
  
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
  
8.  <span data-ttu-id="724db-134">建立並傳送要求訊息。</span><span class="sxs-lookup"><span data-stu-id="724db-134">Create and send the request message.</span></span>  
  
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
  
     <span data-ttu-id="724db-135">在建立要求訊息時，您必須指定表示配接器介面在資料表執行的動作的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="724db-135">While creating the request message, you must specify the message action that indicates the action that the adapter performs on the interface table.</span></span> <span data-ttu-id="724db-136">若要執行插入作業 MS_SAMPLE_EMPLOYEE 資料表上的，為訊息動作`InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`。</span><span class="sxs-lookup"><span data-stu-id="724db-136">To perform an Insert operation on the MS_SAMPLE_EMPLOYEE table, the message action is `InterfaceTables/Insert/FND/APPS/MS_SAMPLE_EMPLOYEE`.</span></span> <span data-ttu-id="724db-137">如需如何判斷在資料表上的各種動作的訊息動作資訊，請參閱[Insert、 Update、 Delete 和選取作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="724db-137">For information about how you can determine the message action for various operations on tables, see [Message Schemas for Insert, Update, Delete, and Select Operations](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md).</span></span>  
  
9. <span data-ttu-id="724db-138">取得回應訊息。</span><span class="sxs-lookup"><span data-stu-id="724db-138">Get the response message.</span></span>  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
10. <span data-ttu-id="724db-139">關閉訊息、 通道和通道處理站。</span><span class="sxs-lookup"><span data-stu-id="724db-139">Close the message, channel, and channel factory.</span></span>  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
11. <span data-ttu-id="724db-140">建置專案。</span><span class="sxs-lookup"><span data-stu-id="724db-140">Build the project.</span></span> <span data-ttu-id="724db-141">建置專案之後, 您必須複製的要求訊息，InsertRequest.xml，在您的專案可執行檔相同的位置。</span><span class="sxs-lookup"><span data-stu-id="724db-141">After building the project, you must copy the request message, InsertRequest.xml, at the same location as your project executable.</span></span> <span data-ttu-id="724db-142">一般而言，這個位置是專案目錄底下的 \bin\Debug\。</span><span class="sxs-lookup"><span data-stu-id="724db-142">Typically, this location is \bin\Debug\ under your project directory.</span></span>  
  
12. <span data-ttu-id="724db-143">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="724db-143">Run the application.</span></span> <span data-ttu-id="724db-144">回應訊息，Response.xml，會儲存您的應用程式中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="724db-144">The response message, Response.xml, is saved at the location you specified in the application.</span></span> <span data-ttu-id="724db-145">回應訊息包含數字或插入的記錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="724db-145">The response message contains the number or records inserted and resembles the following:</span></span>  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE">  
      <InsertResult>1</InsertResult>  
    </InsertResponse>  
    ```  
  
     <span data-ttu-id="724db-146">值"1"代表單一資料錄插入 MS_SAMPLE_EMPLOYEE 資料表。</span><span class="sxs-lookup"><span data-stu-id="724db-146">The value “1” denotes that a single record is inserted into the MS_SAMPLE_EMPLOYEE table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724db-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="724db-147">See Also</span></span>  
 [<span data-ttu-id="724db-148">開發 Oracle E-business Suite 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="724db-148">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
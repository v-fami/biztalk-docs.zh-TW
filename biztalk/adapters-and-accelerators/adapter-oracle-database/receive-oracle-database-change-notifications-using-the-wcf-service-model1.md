---
title: "接收使用 WCF 服務 Model1 Oracle 資料庫的變更通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0f0e2bf-3e76-43cc-85dc-7483dbce1cb5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed8723cef3351420cbe35e0f9fc85d2ba400b410
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications-using-the-wcf-service-model1"></a><span data-ttu-id="cb4ab-102">接收使用 WCF 服務 Model1 Oracle 資料庫的變更通知</span><span class="sxs-lookup"><span data-stu-id="cb4ab-102">Receive Oracle Database Change Notifications Using the WCF Service Model1</span></span>
<span data-ttu-id="cb4ab-103">本主題示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來從 Oracle 資料庫接收查詢通知訊息。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-103">This topic demonstrates how to configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive query notification messages from an Oracle database.</span></span> <span data-ttu-id="cb4ab-104">為了示範通知，請考慮的資料表，ACCOUNTACTIVITY，與 「 處理 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-104">To demonstrate notifications, consider a table, ACCOUNTACTIVITY, with a “Processed” column.</span></span> <span data-ttu-id="cb4ab-105">當新的記錄插入此資料表時，[狀態] 欄的值設定為 ' n '。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-105">When a new record is inserted to this table, the value of the Status column is set to ‘n’.</span></span> <span data-ttu-id="cb4ab-106">您可以設定要接收通知，請使用 SQL 陳述式可擷取所有記錄的 「 處理 」 資料行做為通知註冊配接器 ' n '。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-106">You can configure the adapter to receive notifications by registering for notifications using a SQL statement that retrieves all records that have “Processed” column as ‘n’.</span></span> <span data-ttu-id="cb4ab-107">您可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-107">You can do so by specifying the SQL statement for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="cb4ab-108">一旦配接器用戶端會收到通知，它可以包含執行的 Oracle 資料庫上的任何後續工作的邏輯。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-108">Once the adapter client receives the notification, it can contain the logic to do any subsequent tasks on the Oracle database.</span></span> <span data-ttu-id="cb4ab-109">在此範例中，為了簡單起見，配接器用戶端列出的 「 處理 」 資料行做為資料表中的所有記錄 ' n '。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-109">In this example, for the sake of simplicity, the adapter client lists all the records in the table that have the “Processed” column as ‘n’.</span></span>  
  
## <a name="configuring-notifications-with-the-oracle-database-adapter-binding-properties"></a><span data-ttu-id="cb4ab-110">Oracle 資料庫配接器繫結屬性與設定通知</span><span class="sxs-lookup"><span data-stu-id="cb4ab-110">Configuring Notifications with the Oracle Database Adapter Binding Properties</span></span>  
 <span data-ttu-id="cb4ab-111">下表摘要說明[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結，您用來設定從 Oracle 資料庫接收通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-111">The table below summarizes the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] binding properties that you use to configure receiving notifications from Oracle database.</span></span> <span data-ttu-id="cb4ab-112">您必須執行.NET 應用程式接收通知時指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-112">You must specify these binding properties while running the .NET application to receive notifications.</span></span>  
  
|<span data-ttu-id="cb4ab-113">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="cb4ab-113">Binding Property</span></span>|<span data-ttu-id="cb4ab-114">Description</span><span class="sxs-lookup"><span data-stu-id="cb4ab-114">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="cb4ab-115">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="cb4ab-115">**InboundOperationType**</span></span>|<span data-ttu-id="cb4ab-116">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-116">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="cb4ab-117">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-117">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="cb4ab-118">**NotificationPort**</span><span class="sxs-lookup"><span data-stu-id="cb4ab-118">**NotificationPort**</span></span>|<span data-ttu-id="cb4ab-119">指定 ODP.NET 必須開啟從 Oracle 資料庫的資料庫變更通知所接聽的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-119">Specifies the port number that ODP.NET must open to listen for database change notification from Oracle database.</span></span>|  
|<span data-ttu-id="cb4ab-120">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="cb4ab-120">**NotificationStatement**</span></span>|<span data-ttu-id="cb4ab-121">指定用來註冊查詢通知的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-121">Specifies the SELECT statement used to register for query notifications.</span></span> <span data-ttu-id="cb4ab-122">僅在結果集，指定 SELECT 陳述式變更時，配接器會取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-122">The adapter gets a notification message only when the result set for the specified SELECT statement changes.</span></span>|  
|<span data-ttu-id="cb4ab-123">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="cb4ab-123">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="cb4ab-124">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-124">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="cb4ab-125">如需這些屬性的更完整說明，請參閱[Oracle 資料庫的設定繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-125">For a more complete description of these properties, see [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).</span></span> <span data-ttu-id="cb4ab-126">如需完整的說明，如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]進一步若要從 Oracle 資料庫接收通知，閱讀。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-126">For a complete description of how to use the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive notifications from Oracle database, read further.</span></span>  
  
## <a name="configuring-notifications-using-the-wcf-service-model"></a><span data-ttu-id="cb4ab-127">設定通知使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="cb4ab-127">Configuring Notifications Using the WCF Service Model</span></span>  
 <span data-ttu-id="cb4ab-128">若要接收通知使用 WCF 服務模型，您必須：</span><span class="sxs-lookup"><span data-stu-id="cb4ab-128">To receive the notifications using the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="cb4ab-129">產生 WCF 服務合約 （介面）**通知**從配接器所公開的中繼資料的作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-129">Generate a WCF service contract (interface) for the **Notification** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="cb4ab-130">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-130">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="cb4ab-131">產生的 WCF 用戶端**選取**ACCOUNTACTIVITY 資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-131">Generate a WCF client for the **Select** operation on the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="cb4ab-132">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-132">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
-   <span data-ttu-id="cb4ab-133">實作這個介面從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-133">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="cb4ab-134">裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-134">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="cb4ab-135">WCF 服務合約和類別</span><span class="sxs-lookup"><span data-stu-id="cb4ab-135">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="cb4ab-136">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-136">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Notification** operation.</span></span> <span data-ttu-id="cb4ab-137">如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-137">For more information about generating a WCF service contract, see [Generate a WCF client or a WCF service contract for Oracle Database solution artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="cb4ab-138">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="cb4ab-138">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="cb4ab-139">下列程式碼顯示產生的 WCF 服務合約 （介面）**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-139">The following code shows the WCF service contract (interface) generated for the **Notification** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="Notification_OperationGroup")]  
public interface Notification_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/Notification/) of message Notification  
    // does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/Notification")]  
    void Notification(Notification request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="cb4ab-140">訊息合約</span><span class="sxs-lookup"><span data-stu-id="cb4ab-140">The Message Contracts</span></span>  
 <span data-ttu-id="cb4ab-141">以下是通知作業的訊息合約。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-141">Following is the message contract for the Notification operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.Notification.NotificationDetails[] Details;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=1)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=2)]  
    public string[] ResourceNames;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=3)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/Notification/", Order=4)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(microsoft.lobservices.oracledb._2007._03.Notification.NotificationDetails[] Details, string Info, string[] ResourceNames, string Source, string Type) {  
        this.Details = Details;  
        this.Info = Info;  
        this.ResourceNames = ResourceNames;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="cb4ab-142">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="cb4ab-142">WCF Service Class</span></span>  
 <span data-ttu-id="cb4ab-143">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-143">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="cb4ab-144">檔案的名稱是 OracleDBBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-144">The name of the file is OracleDBBindingService.cs.</span></span> <span data-ttu-id="cb4ab-145">您可以插入要處理邏輯**通知**直接將這個類別的作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-145">You can insert the logic to process the **Notification** operation directly into this class.</span></span> <span data-ttu-id="cb4ab-146">下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-146">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : Notification_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/Notification/) of message Notification  
        // does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-database-change-notifications-using-wcf-service-model"></a><span data-ttu-id="cb4ab-147">使用 WCF 服務模型的接收資料庫變更通知</span><span class="sxs-lookup"><span data-stu-id="cb4ab-147">Receiving Database Change Notifications Using WCF Service Model</span></span>  
 <span data-ttu-id="cb4ab-148">本節說明如何撰寫.NET 應用程式接收查詢通知使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-148">This section provides instructions on how to write a .NET application to receive query notifications using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
#### <a name="to-receive-query-notifications"></a><span data-ttu-id="cb4ab-149">若要接收查詢通知</span><span class="sxs-lookup"><span data-stu-id="cb4ab-149">To receive query notifications</span></span>  
  
1.  <span data-ttu-id="cb4ab-150">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端**選取**作業**ACCOUNTACTIVITY**資料表。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-150">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client for **Select** operation on the **ACCOUNTACTIVITY** table.</span></span> <span data-ttu-id="cb4ab-151">您將使用此用戶端來接收通知訊息之後，執行 Select 作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-151">You will use this client to perform Select operations after receiving a notification message.</span></span> <span data-ttu-id="cb4ab-152">加入新的類別，TableOperation.cs 至您的專案並加入下列程式碼片段來執行選取的作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-152">Add a new class, TableOperation.cs to your project and add the following code snippet to perform a Select operation.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace Notification_ServiceModel  
    {  
        class TableOperation  
        {  
            public void TableOp()  
            {  
                //////////////////////////////////////////////////////////////////////  
                // CREATING THE CLIENT AND SETTING CLIENT CREDENTIALS  
                //////////////////////////////////////////////////////////////////////  
  
                SCOTT_Table_ACCOUNTACTIVITYClient client = new SCOTT_Table_ACCOUNTACTIVITYClient("OracleDBBinding_SCOTT_Table_ACCOUNTACTIVITY");  
                client.ClientCredentials.UserName.UserName = "SCOTT";  
                client.ClientCredentials.UserName.Password = "TIGER";  
  
                ////////////////////////////////////////////////////////////////////  
                // OPENING THE CLIENT  
                //////////////////////////////////////////////////////////////////////  
                try  
                {  
                    Console.WriteLine("Opening the client ...");  
                    client.Open();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                ////////////////////////////////////////////////////////////////////////////////////////  
                // SELECTING THE LAST INSERTED VALUE  
                ////////////////////////////////////////////////////////////////////////////////////////  
  
                Console.WriteLine("The application will now select the last inserted record");  
  
                microsoft.lobservices.oracledb._2007._03.SCOTT.Table.ACCOUNTACTIVITY.ACCOUNTACTIVITYRECORDSELECT[] selectRecords;  
  
                try  
                {  
                    selectRecords = client.Select("*", "WHERE PROCESSED = 'n'");  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                Console.WriteLine("The details of the newly added records are:");  
                Console.WriteLine("********************************************");  
                for (int i = 0; i < selectRecords.Length; i++)  
                {  
                    Console.WriteLine("Transaction ID   : " + selectRecords[i].TID);  
                    Console.WriteLine("Account ID       : " + selectRecords[i].ACCOUNT);  
                    Console.WriteLine("Processed Status : " + selectRecords[i].PROCESSED);  
                    Console.WriteLine();  
                }  
                Console.WriteLine("********************************************");  
            }  
        }  
    }  
  
    ```  
  
2.  <span data-ttu-id="cb4ab-153">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-153">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Notification** operation.</span></span>  
  
     <span data-ttu-id="cb4ab-154">如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-154">For more information, see [Generate a WCF client or a WCF service contract for Oracle Database solution artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span> <span data-ttu-id="cb4ab-155">您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-155">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="cb4ab-156">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-156">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
3.  <span data-ttu-id="cb4ab-157">實作 WCF 服務，從步驟 2 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-157">Implement a WCF service from the interface and helper classes generated in step 2.</span></span> <span data-ttu-id="cb4ab-158">**通知**這個類別的方法可以擲回例外狀況可中止此作業，處理從接收的資料發生錯誤**通知**作業; 否則方法會執行不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-158">The **Notification** method of this class can throw an exception to abort the operation, if an error is encountered processing the data received from the **Notification** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="cb4ab-159">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb4ab-159">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="cb4ab-160">內**通知**方法，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-160">Within the **Notification** method, you can implement your application logic directly.</span></span> <span data-ttu-id="cb4ab-161">這個類別可以 OracleDBBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-161">This class can be found in OracleDBBindingService.cs.</span></span> <span data-ttu-id="cb4ab-162">這段程式碼，在此範例中的子類別**OracleDBBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-162">This code in this example sub-classes the **OracleDBBindingService** class.</span></span> <span data-ttu-id="cb4ab-163">在此程式碼中，接收的通知訊息會寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-163">In this code, the notification message received is written to the console.</span></span> <span data-ttu-id="cb4ab-164">此外， **TableOp**方法內**TableOperation**類別會叫用來執行選取的作業。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-164">Additionally, the **TableOp** method within the **TableOperation** class is invoked to perform the Select operation.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
        public class NotificationService : OracleDBBindingNamespace.OracleDBBindingService  
        {  
            public override void Notification(Notification request)  
            {  
                Console.WriteLine("\nNew Notification Received");  
                Console.WriteLine("*************************************************");  
                Console.WriteLine(request.Info);  
                Console.WriteLine(request.Source);  
                Console.WriteLine(request.Type);  
                Console.WriteLine("*************************************************");  
  
                TableOperation Ops = new TableOperation();  
                Ops.TableOp();  
  
            }  
        }  
    ```  
  
4.  <span data-ttu-id="cb4ab-165">您必須實作下列類別，以將 Oracle 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-165">You must implement the following class to pass credentials for the Oracle database.</span></span> <span data-ttu-id="cb4ab-166">在應用程式的第二個部分中，您會具現化這個類別，以傳遞的認證。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-166">In the latter part of the application, you will instantiate this class to pass on the credentials.</span></span>  
  
    ```  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="cb4ab-167">建立**OracleDBBinding**和設定介面卡接收查詢通知所指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-167">Create an **OracleDBBinding** and configure the adapter to receive query notifications by specifying the binding properties.</span></span> <span data-ttu-id="cb4ab-168">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-168">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="cb4ab-169">最少，您必須指定**InboundOperationType**和**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-169">At a minimum, you must specify the **InboundOperationType** and **NotificationStatement** binding properties.</span></span>  
  
    ```  
    OracleDBBinding binding = new OracleDBBinding();  
    binding.InboundOperationType = InboundOperation.Notification;  
    binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
    binding.NotifyOnListenerStart = true;  
    binding.NotificationPort = 10;  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cb4ab-170">值**NotificationPort**繫結屬性必須設定為相同的連接埠號碼，您必須已加入 Windows 防火牆例外清單。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-170">The value for the **NotificationPort** binding property must be set to the same port number that you must have added to the Windows Firewall exceptions list.</span></span> <span data-ttu-id="cb4ab-171">如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkId=196959](http://go.microsoft.com/fwlink/?LinkId=196959)。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-171">For instructions on how to add ports to Windows Firewall exceptions list, see [http://go.microsoft.com/fwlink/?LinkId=196959](http://go.microsoft.com/fwlink/?LinkId=196959).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cb4ab-172">如果您未設定**NotificationPort**繫結屬性，配接器將假設使用預設值為-1，此繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-172">If you do not set the **NotificationPort** binding property, the adapter will assume the default value of -1 for this binding property.</span></span> <span data-ttu-id="cb4ab-173">在這種情況下，您必須完全停用 Windows 防火牆來接收通知訊息。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-173">In such a case, you will have to completely disable Windows Firewall to receive notification messages.</span></span>  
  
6.  <span data-ttu-id="cb4ab-174">指定 Oracle 資料庫認證，藉由執行個體化**NotificationCredentials**您在步驟 4 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-174">Specify Oracle database credentials by instantiating the **NotificationCredentials** class you created in Step 4.</span></span>  
  
    ```  
    NotificationCredentials credentials = new NotificationCredentials();  
    credentials.UserName.UserName = "SCOTT";  
    credentials.UserName.Password = "TIGER";  
    ```  
  
7.  <span data-ttu-id="cb4ab-175">建立在步驟 3 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-175">Create an instance of the WCF service created in step 3.</span></span>  
  
    ```  
    // create service instance  
    NotificationService service = new NotificationService();  
    ```  
  
8.  <span data-ttu-id="cb4ab-176">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-176">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="cb4ab-177">您也必須指定的認證。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-177">You must also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracledb://adapter") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. <span data-ttu-id="cb4ab-178">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-178">Add a service endpoint to the service host.</span></span> <span data-ttu-id="cb4ab-179">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="cb4ab-179">To do this:</span></span>  
  
    -   <span data-ttu-id="cb4ab-180">使用步驟 5 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-180">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="cb4ab-181">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-181">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="cb4ab-182">為 「 Notification_OperationGroup"指定的合約。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-182">Specify the contract as "Notification_OperationGroup".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify Notification_OperationGroup as the contract  
    Uri ConnectionUri = new Uri("oracledb://adapter");  
    serviceHost.AddServiceEndpoint("Notification_OperationGroup", binding, ConnectionUri);  
    ```  
  
10. <span data-ttu-id="cb4ab-183">若要收到通知訊息，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-183">To receive notification message, open the service host.</span></span>  
  
    ```  
    // Open the service host to begin receiving notifications  
    serviceHost.Open();  
    ```  
  
11. <span data-ttu-id="cb4ab-184">若要停止接收通知，請關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-184">To stop receiving notifications, close the service host.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="cb4ab-185">範例</span><span class="sxs-lookup"><span data-stu-id="cb4ab-185">Example</span></span>  
 <span data-ttu-id="cb4ab-186">下列範例會示範.NET 應用程式來接收通知訊息 ACCOUNTACTIVITY 資料表。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-186">The following example shows a .NET application to receive notification messages for the ACCOUNTACTIVITY table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb4ab-187">下列程式碼片段會具現化**TableOperation.cs**類別，並叫用**TableOp**方法。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-187">The following code snippet instantiates a **TableOperation.cs** class and invokes the **TableOp** method.</span></span> <span data-ttu-id="cb4ab-188">在步驟 1 中描述的類別和方法。</span><span class="sxs-lookup"><span data-stu-id="cb4ab-188">The class and the method are described in Step 1.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.Adapters.OracleDB;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : OracleDBBindingNamespace.OracleDBBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
  
        }  
    }  
  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;  
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start receiving notifications...");  
                Console.ReadLine();  
  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT TID,ACCOUNT,PROCESSED FROM APPS.ACCOUNTACTIVITY WHERE PROCESSED = 'n'";  
                binding.NotifyOnListenerStart = true;  
                binding.NotificationPort = 10;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracledb://adapter");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracledb://adapter") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "SCOTT";  
                credentials.UserName.Password = "TIGER";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("Notification_OperationGroup", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Waiting for notification...");  
  
                Console.WriteLine("\nHit <RETURN> to stop receiving notification");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb4ab-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb4ab-189">See Also</span></span>  
 [<span data-ttu-id="cb4ab-190">開發使用 WCF 服務模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="cb4ab-190">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)
---
title: 使用 WCF 服務模型的 sql 接收查詢通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c9def31-3c5a-4326-b798-31bde0ff2568
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b21d2123b646a02669a9da65efc5069931e64c69
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964084"
---
# <a name="receive-query-notifications-from-sql-using-the-wcf-service-model"></a><span data-ttu-id="76ff9-102">使用 WCF 服務模型的 sql 接收查詢通知</span><span class="sxs-lookup"><span data-stu-id="76ff9-102">Receive Query Notifications from SQL using the WCF Service Model</span></span>
<span data-ttu-id="76ff9-103">本主題示範如何設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收查詢通知訊息從 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="76ff9-103">This topic demonstrates how to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notification messages from a SQL Server database.</span></span> <span data-ttu-id="76ff9-104">為了示範通知，請考慮的資料表，員工與 「 狀態 」 資料行。</span><span class="sxs-lookup"><span data-stu-id="76ff9-104">To demonstrate notifications, consider a table, Employee, with a “Status” column.</span></span> <span data-ttu-id="76ff9-105">當新的記錄插入此資料表時，[狀態] 欄的值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="76ff9-105">When a new record is inserted to this table, the value of the Status column is set to 0.</span></span> <span data-ttu-id="76ff9-106">您可以設定配接器接收通知，請註冊通知使用 SQL 陳述式可擷取所有記錄狀態 欄位為"0"。</span><span class="sxs-lookup"><span data-stu-id="76ff9-106">You can configure the adapter to receive notifications by registering for notifications using a SQL statement that retrieves all records that have Status column as “0.”</span></span> <span data-ttu-id="76ff9-107">您可以藉由指定的 SQL 陳述式**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="76ff9-107">You can do so by specifying the SQL statement for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="76ff9-108">配接器用戶端會收到通知之後，它可以包含執行 SQL Server 資料庫上的任何後續工作的邏輯。</span><span class="sxs-lookup"><span data-stu-id="76ff9-108">After the adapter client receives the notification, it can contain the logic to do any subsequent tasks on the SQL Server database.</span></span> <span data-ttu-id="76ff9-109">在此範例中，為了簡單起見，配接器用戶端會列出所有記錄資料表中的，[狀態] 欄為"0"。</span><span class="sxs-lookup"><span data-stu-id="76ff9-109">In this example, for the sake of simplicity, the adapter client lists all the records in the table that have the Status column as “0.”</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76ff9-110">如果您正在執行具有使用者定義類型的資料行的資料表上的作業，請確定您參考[資料表和檢視表上使用 SQL 配接器的使用者定義類型的作業](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md)開始開發應用程式之前的主題.</span><span class="sxs-lookup"><span data-stu-id="76ff9-110">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on tables and views with user-defined types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) topic before you start developing your application.</span></span>  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="76ff9-111">使用 SQL 配接器繫結屬性中設定通知</span><span class="sxs-lookup"><span data-stu-id="76ff9-111">Configuring Notifications with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="76ff9-112">下表摘要說明[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]繫結，您用來設定 SQL Server 從接收通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="76ff9-112">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure receiving notifications from SQL Server.</span></span> <span data-ttu-id="76ff9-113">您必須執行.NET 應用程式要從 SQL Server 資料庫接收通知時指定這些繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="76ff9-113">You must specify these binding properties while running the .NET application to receive the notifications from a SQL Server database.</span></span>  
  
|<span data-ttu-id="76ff9-114">繫結屬性</span><span class="sxs-lookup"><span data-stu-id="76ff9-114">Binding Property</span></span>|<span data-ttu-id="76ff9-115">Description</span><span class="sxs-lookup"><span data-stu-id="76ff9-115">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="76ff9-116">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="76ff9-116">**InboundOperationType**</span></span>|<span data-ttu-id="76ff9-117">指定輸入您想要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-117">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="76ff9-118">若要接收通知訊息，將此設**通知**。</span><span class="sxs-lookup"><span data-stu-id="76ff9-118">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="76ff9-119">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="76ff9-119">**NotificationStatement**</span></span>|<span data-ttu-id="76ff9-120">指定的 SQL 陳述式 (SELECT 或 EXEC \<*預存程序*\>) 用來註冊查詢通知。</span><span class="sxs-lookup"><span data-stu-id="76ff9-120">Specifies the SQL statement (SELECT or EXEC \<*stored procedure*\>) used to register for query notifications.</span></span> <span data-ttu-id="76ff9-121">在結果集為指定的 SQL 陳述式變更時，才配接器從 SQL Server 取得通知訊息。</span><span class="sxs-lookup"><span data-stu-id="76ff9-121">The adapter gets a notification message from SQL Server only when the result set for the specified SQL statement changes.</span></span>|  
|<span data-ttu-id="76ff9-122">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="76ff9-122">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="76ff9-123">指定是否配接器傳送通知給配接器用戶端啟動接聽程式時。</span><span class="sxs-lookup"><span data-stu-id="76ff9-123">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="76ff9-124">如需這些屬性的更完整說明，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="76ff9-124">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="76ff9-125">如需完整的說明，如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]進一步要從 SQL Server 中接收通知，閱讀。</span><span class="sxs-lookup"><span data-stu-id="76ff9-125">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notifications from SQL Server, read further.</span></span>  
  
## <a name="configuring-notifications-using-the-wcf-service-model"></a><span data-ttu-id="76ff9-126">設定通知使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="76ff9-126">Configuring Notifications Using the WCF Service Model</span></span>  
 <span data-ttu-id="76ff9-127">若要接收通知使用 WCF 服務模型，您必須：</span><span class="sxs-lookup"><span data-stu-id="76ff9-127">To receive the notifications using the WCF service model, you must:</span></span>  
  
1.  <span data-ttu-id="76ff9-128">產生 WCF 服務合約 （介面）**通知**從配接器所公開的中繼資料的作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-128">Generate a WCF service contract (interface) for the **Notification** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="76ff9-129">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76ff9-129">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
2.  <span data-ttu-id="76ff9-130">產生的 WCF 用戶端**選取**員工資料表上的作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-130">Generate a WCF client for the **Select** operation on the Employee table.</span></span> <span data-ttu-id="76ff9-131">若要這樣做，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76ff9-131">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
3.  <span data-ttu-id="76ff9-132">實作這個介面從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="76ff9-132">Implement a WCF service from this interface.</span></span>  
  
4.  <span data-ttu-id="76ff9-133">裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。</span><span class="sxs-lookup"><span data-stu-id="76ff9-133">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="76ff9-134">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="76ff9-134">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="76ff9-135">本主題中的範例接收 Employee 資料表的通知。</span><span class="sxs-lookup"><span data-stu-id="76ff9-135">The examples in this topic receive notification for the Employee table.</span></span> <span data-ttu-id="76ff9-136">若要產生資料表的指令碼會提供範例。</span><span class="sxs-lookup"><span data-stu-id="76ff9-136">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="76ff9-137">如需這些範例的詳細資訊，請參閱[SQL 配接器範例](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="76ff9-137">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="76ff9-138">範例中， **Notification_ServiceModel**，根據本主題中，也會提供與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="76ff9-138">A sample, **Notification_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="76ff9-139">WCF 服務合約和類別</span><span class="sxs-lookup"><span data-stu-id="76ff9-139">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="76ff9-140">您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 服務合約 （介面） 和支援類別**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-140">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Notification** operation.</span></span> <span data-ttu-id="76ff9-141">如需產生 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="76ff9-141">For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="76ff9-142">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="76ff9-142">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="76ff9-143">下列程式碼顯示產生的 WCF 服務合約 （介面）**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-143">The following code shows the WCF service contract (interface) generated for the **Notification** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="NotificationOperation")]  
public interface NotificationOperation {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Notification/) of message  
    // Notification does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Notification")]  
    void Notification(Notification request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="76ff9-144">訊息合約</span><span class="sxs-lookup"><span data-stu-id="76ff9-144">The Message Contracts</span></span>  
 <span data-ttu-id="76ff9-145">以下是通知作業的訊息合約。</span><span class="sxs-lookup"><span data-stu-id="76ff9-145">Following is the message contract for the Notification operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=0)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=1)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=2)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(string Info, string Source, string Type) {  
        this.Info = Info;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="76ff9-146">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="76ff9-146">WCF Service Class</span></span>  
 <span data-ttu-id="76ff9-147">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。</span><span class="sxs-lookup"><span data-stu-id="76ff9-147">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="76ff9-148">檔案的名稱是 SqlAdapterBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="76ff9-148">The name of the file is SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="76ff9-149">您可以插入要處理邏輯**通知**直接將這個類別的作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-149">You can insert the logic to process the **Notification** operation directly into this class.</span></span> <span data-ttu-id="76ff9-150">下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76ff9-150">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : NotificationOperation {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Notification/)   
        // of message Notification does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-query-notifications-using-wcf-service-model"></a><span data-ttu-id="76ff9-151">使用 WCF 服務模型的接收查詢通知</span><span class="sxs-lookup"><span data-stu-id="76ff9-151">Receiving Query Notifications Using WCF Service Model</span></span>  
 <span data-ttu-id="76ff9-152">本節說明如何撰寫.NET 應用程式接收查詢通知使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="76ff9-152">This section provides instructions on how to write a .NET application to receive query notifications using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
#### <a name="to-receive-query-notifications"></a><span data-ttu-id="76ff9-153">若要接收查詢通知</span><span class="sxs-lookup"><span data-stu-id="76ff9-153">To receive query notifications</span></span>  
  
1.  <span data-ttu-id="76ff9-154">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 用戶端**選取**作業**員工**資料表。</span><span class="sxs-lookup"><span data-stu-id="76ff9-154">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client for **Select** operation on the **Employee** table.</span></span> <span data-ttu-id="76ff9-155">您將使用此用戶端來接收通知訊息之後，執行 Select 作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-155">You will use this client to perform Select operations after receiving a notification message.</span></span> <span data-ttu-id="76ff9-156">加入新的類別，TableOperation.cs 至您的專案並加入下列程式碼片段來執行選取的作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-156">Add a new class, TableOperation.cs to your project and add the following code snippet to perform a Select operation.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace Notification_ServiceModel  
    {  
        public class TableOperation  
        {  
            public void TableOp()  
            {  
                ///////////////////////////////////////////////////////////////////////  
                // CREATING THE CLIENT  
                ///////////////////////////////////////////////////////////////////////  
  
                TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
  
                client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
                client.ClientCredentials.UserName.Password = "<Enter password here>";  
  
                ///////////////////////////////////////////////////////////////////////  
                // OPENING THE CLIENT  
                ///////////////////////////////////////////////////////////////////////  
  
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
  
                ///////////////////////////////////////////////////////////////////////  
                // SELECTING THE LAST INSERTED RECORD FROM THE TABLE  
                ///////////////////////////////////////////////////////////////////////  
                schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
                try  
                {  
                    selectRecords = client.Select("*", "where Status=0");  
                }  
  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                Console.WriteLine("The details of the newly added employee are:");  
                Console.WriteLine("********************************************");  
                for (int i = 0; i < selectRecords.Length; i++)  
                {  
                    Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
                    Console.WriteLine("Employee Designation: " + selectRecords[i].Designation);  
                    Console.WriteLine("Employee Status    : " + selectRecords[i].Status);  
                    Console.WriteLine();  
                }  
                Console.WriteLine("********************************************");  
  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="76ff9-157">因為此程式碼片段會執行包含 Point UDT 資料行的員工資料表上的作業，請確定您專案的 \bin\Debug 資料夾下放置 UDT DLL 時執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="76ff9-157">Because this code snippet performs operations on the Employee table that contains a Point UDT column, make sure you put the UDT DLL under the project’s \bin\Debug folder while running the application.</span></span>  
  
2.  <span data-ttu-id="76ff9-158">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生 WCF 服務合約 （介面） 和協助程式類別，如**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-158">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Notification** operation.</span></span>  
  
     <span data-ttu-id="76ff9-159">如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="76ff9-159">For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span> <span data-ttu-id="76ff9-160">您可以選擇性地產生服務合約和協助程式類別時指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="76ff9-160">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="76ff9-161">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="76ff9-161">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
3.  <span data-ttu-id="76ff9-162">實作 WCF 服務，從步驟 2 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="76ff9-162">Implement a WCF service from the interface and helper classes generated in step 2.</span></span> <span data-ttu-id="76ff9-163">**通知**這個類別的方法可以擲回例外狀況可中止此作業，處理從接收的資料發生錯誤**通知**作業; 否則方法會執行不會傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="76ff9-163">The **Notification** method of this class can throw an exception to abort the operation, if an error is encountered processing the data received from the **Notification** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="76ff9-164">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="76ff9-164">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="76ff9-165">內**通知**方法，您可以直接實作應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="76ff9-165">Within the **Notification** method, you can implement your application logic directly.</span></span> <span data-ttu-id="76ff9-166">這個類別可以 SqlAdapterBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="76ff9-166">This class can be found in SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="76ff9-167">這段程式碼，在此範例中的子類別**SqlAdapterBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="76ff9-167">This code in this example sub-classes the **SqlAdapterBindingService** class.</span></span> <span data-ttu-id="76ff9-168">在此程式碼中，接收的通知訊息會寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="76ff9-168">In this code, the notification message received is written to the console.</span></span> <span data-ttu-id="76ff9-169">此外， **TableOp**方法內**TableOperation**類別會叫用來執行選取的作業。</span><span class="sxs-lookup"><span data-stu-id="76ff9-169">Additionally, the **TableOp** method within the **TableOperation** class is invoked to perform the Select operation.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            // Invoke th TableOp method in the TableOperation class  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="76ff9-170">因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]未接受認證的連線 URI 的一部分，您必須實作下列類別，以 SQL Server 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="76ff9-170">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database.</span></span> <span data-ttu-id="76ff9-171">在應用程式的第二個部分中，您會具現化這個類別，以對 SQL Server 認證。</span><span class="sxs-lookup"><span data-stu-id="76ff9-171">In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.</span></span>  
  
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
  
5.  <span data-ttu-id="76ff9-172">建立**SqlAdapterBinding**和設定介面卡接收查詢通知所指定的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="76ff9-172">Create a **SqlAdapterBinding** and configure the adapter to receive query notifications by specifying the binding properties.</span></span> <span data-ttu-id="76ff9-173">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="76ff9-173">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="76ff9-174">最少，您必須指定**InboundOperationType**和**NotificationStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="76ff9-174">At a minimum, you must specify the **InboundOperationType** and **NotificationStatement** binding properties.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Notification;  
    binding.NotificationStatement = "SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0";  
    binding.NotifyOnListenerStart = true;  
    ```  
  
6.  <span data-ttu-id="76ff9-175">指定 SQL Server 資料庫認證，藉由執行個體化**NotificationCredentials**您在步驟 4 中建立的類別。</span><span class="sxs-lookup"><span data-stu-id="76ff9-175">Specify SQL Server database credentials by instantiating the **NotificationCredentials** class you created in Step 4.</span></span>  
  
    ```  
    NotificationCredentials credentials = new NotificationCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
7.  <span data-ttu-id="76ff9-176">建立在步驟 3 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="76ff9-176">Create an instance of the WCF service created in step 3.</span></span>  
  
    ```  
    // create service instance  
    NotificationService service = new NotificationService();  
    ```  
  
8.  <span data-ttu-id="76ff9-177">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="76ff9-177">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="76ff9-178">您也必須指定的認證。</span><span class="sxs-lookup"><span data-stu-id="76ff9-178">You must also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. <span data-ttu-id="76ff9-179">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="76ff9-179">Add a service endpoint to the service host.</span></span> <span data-ttu-id="76ff9-180">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="76ff9-180">To do this:</span></span>  
  
    -   <span data-ttu-id="76ff9-181">使用步驟 5 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="76ff9-181">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="76ff9-182">指定連線 URI，其中包含認證並在必要時輸入的識別碼。</span><span class="sxs-lookup"><span data-stu-id="76ff9-182">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="76ff9-183">為 「 NotificationOperation"指定的合約。</span><span class="sxs-lookup"><span data-stu-id="76ff9-183">Specify the contract as "NotificationOperation".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify NotificationOperation as the contract  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    serviceHost.AddServiceEndpoint("NotificationOperation", binding, ConnectionUri);  
    ```  
  
10. <span data-ttu-id="76ff9-184">若要收到通知訊息，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="76ff9-184">To receive notification message, open the service host.</span></span>  
  
    ```  
    // Open the service host to begin receiving notifications  
    serviceHost.Open();  
    ```  
  
11. <span data-ttu-id="76ff9-185">若要停止接收通知，請關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="76ff9-185">To stop receiving notifications, close the service host.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="76ff9-186">範例</span><span class="sxs-lookup"><span data-stu-id="76ff9-186">Example</span></span>  
 <span data-ttu-id="76ff9-187">下列範例會示範.NET 應用程式來接收 Employee 資料表的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="76ff9-187">The following example shows a .NET application to receive notification messages for the Employee table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76ff9-188">下列程式碼片段會具現化**TableOperation.cs**類別，並叫用**TableOp**方法。</span><span class="sxs-lookup"><span data-stu-id="76ff9-188">The following code snippet instantiates a **TableOperation.cs** class and invokes the **TableOp** method.</span></span> <span data-ttu-id="76ff9-189">在步驟 1 中描述的類別和方法。</span><span class="sxs-lookup"><span data-stu-id="76ff9-189">The class and the method are described in Step 1.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.Sql;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class NotificationService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
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
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0";  
                binding.NotifyOnListenerStart = true;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId (if any) that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // a query_string (InboundID); otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("NotificationOperation", binding, ConnectionUri);  
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
  
                // If there is an error it will be specified in the inner exception   
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop receiving notifications  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="76ff9-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="76ff9-190">See Also</span></span>  
[<span data-ttu-id="76ff9-191">開發 SQL 應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="76ff9-191">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)
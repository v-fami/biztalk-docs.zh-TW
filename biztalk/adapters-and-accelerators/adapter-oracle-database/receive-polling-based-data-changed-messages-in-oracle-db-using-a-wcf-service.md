---
title: "在 Oracle 資料庫中使用 WCF 服務模型收到輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving polling-based messages
- how to, receive polling-based message
- polling-based messages, receiving by using the WCF service model
ms.assetid: 0324e8bf-d9d1-46f5-b896-b9fc8e61d514
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd36081bd92c3bfae13916ed7d984fcd5de9763f
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="f1142-102">在 Oracle 資料庫中使用 WCF 服務模型收到輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="f1142-102">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="f1142-103">您可以設定[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]接收輪詢基礎資料變更的訊息時所依據的 Oracle 資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="f1142-103">You can configure the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to receive polling-based data changed messages against an Oracle table or view.</span></span> <span data-ttu-id="f1142-104">若要接收的資料變更的訊息，配接器會定期執行的 Oracle 資料表或檢視，後面接著選擇性的 PL/SQL 程式碼區塊的 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="f1142-104">To receive data-changed messages, the adapter periodically executes a SQL query against an Oracle table or view followed by an optional PL/SQL code block.</span></span> <span data-ttu-id="f1142-105">SQL 查詢的結果則會傳回由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]為強類型的結果集，傳入的 POLLINGSTMT 作業的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f1142-105">The results of the SQL query are then returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to your application as a strongly-typed result set in an inbound POLLINGSTMT operation.</span></span> <span data-ttu-id="f1142-106">如需有關用來設定和執行 oracle 輪詢機制資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[在 Oracle 資料庫配接器收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f1142-106">For more information about the mechanism used to configure and perform polling on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span> <span data-ttu-id="f1142-107">我們強烈建議您先閱讀本主題後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f1142-107">We strongly recommended that you read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="f1142-108">若要接收 POLLINGSTMT 作業，當您使用 WCF 服務模型時，您必須：</span><span class="sxs-lookup"><span data-stu-id="f1142-108">To receive the POLLINGSTMT operation when you use the WCF service model, you must:</span></span>  
  
-   <span data-ttu-id="f1142-109">POLLINGSTMT 作業從配接器所公開的中繼資料產生 WCF 服務合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="f1142-109">Generate a WCF service contract (interface) for the POLLINGSTMT operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="f1142-110">若要這樣做，您使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe)。</span><span class="sxs-lookup"><span data-stu-id="f1142-110">To do this, you use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe).</span></span>  
  
-   <span data-ttu-id="f1142-111">實作這個介面從 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="f1142-111">Implement a WCF service from this interface.</span></span>  
  
-   <span data-ttu-id="f1142-112">裝載此 WCF 服務，使用服務主機 (**system.servicemodel.servicehost 內**)。</span><span class="sxs-lookup"><span data-stu-id="f1142-112">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
 <span data-ttu-id="f1142-113">此章節的主題提供資訊和程序可協助您對 Oracle 資料庫資料表和檢視 WCF 服務模型中的輪詢。</span><span class="sxs-lookup"><span data-stu-id="f1142-113">The topics in this section provide information and procedures to help you perform polling on Oracle database tables and views in the WCF service model.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="f1142-114">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="f1142-114">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="f1142-115">本主題中的範例使用 /SCOTT/ACCOUNTACTIVITY 資料表和 /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY 函式。</span><span class="sxs-lookup"><span data-stu-id="f1142-115">The examples in this topic use the /SCOTT/ACCOUNTACTIVITY table and the /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY function.</span></span> <span data-ttu-id="f1142-116">指令碼來產生這些成品隨附[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="f1142-116">A script to generate these artifacts is supplied with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] samples.</span></span> <span data-ttu-id="f1142-117">如需這些範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f1142-117">For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a><span data-ttu-id="f1142-118">在 WCF 服務模型中設定輪詢</span><span class="sxs-lookup"><span data-stu-id="f1142-118">Configuring Polling in the WCF Service Model</span></span>  
 <span data-ttu-id="f1142-119">您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]進行輪詢 Oracle 資料庫資料表和檢視表，藉由設定繫結屬性和選用的連接屬性 （參數）。</span><span class="sxs-lookup"><span data-stu-id="f1142-119">You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to perform polling on Oracle database tables and views by setting binding properties and an optional connection property (parameter).</span></span> <span data-ttu-id="f1142-120">其中部分屬性是必要項，並造成影響的部分必須在設計階段和執行階段設定。</span><span class="sxs-lookup"><span data-stu-id="f1142-120">Some of these properties are mandatory, and some, to have an effect, must be set both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="f1142-121">在設計階段，您可以設定連線參數和繫結屬性當您連接到 Oracle 資料庫產生的 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="f1142-121">At design-time, you set connection parameters and binding properties when you connect to the Oracle Database to generate a WCF service contract.</span></span>  
  
-   <span data-ttu-id="f1142-122">在執行階段中，您可以設定繫結屬性 OracleDBBinding 物件您用來建立服務主機上。</span><span class="sxs-lookup"><span data-stu-id="f1142-122">At runtime you set binding properties on the OracleDBBinding object that you use to create the service host.</span></span> <span data-ttu-id="f1142-123">當您將服務的接聽程式加入至服務主機，您可以設定連線參數。</span><span class="sxs-lookup"><span data-stu-id="f1142-123">You set the connection parameter when you add a service listener to the service host.</span></span>  
  
 <span data-ttu-id="f1142-124">下列清單提供的繫結屬性和連接參數用來設定輪詢的簡短概觀：</span><span class="sxs-lookup"><span data-stu-id="f1142-124">The following list provides a brief overview of the binding properties and connection parameters used to configure polling:</span></span>  
  
-   <span data-ttu-id="f1142-125">**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-125">The **PollingStatement** binding property.</span></span> <span data-ttu-id="f1142-126">在設計階段和執行階段，您必須設定這個繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-126">You must set this binding property both at design-time and at run-time.</span></span>  
  
-   <span data-ttu-id="f1142-127">選擇性的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-127">Optional binding properties.</span></span> <span data-ttu-id="f1142-128">這些只需要在執行階段進行設定。</span><span class="sxs-lookup"><span data-stu-id="f1142-128">These only have to be set at run-time.</span></span>  
  
-   <span data-ttu-id="f1142-129">**AcceptCredentialsInUri**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-129">The **AcceptCredentialsInUri** binding property.</span></span> <span data-ttu-id="f1142-130">您必須設定這個繫結屬性為**true**期間執行階段如果您想要讓連線 URI 中的認證。</span><span class="sxs-lookup"><span data-stu-id="f1142-130">You must set this binding property to **true** during run-time if you want to enable credentials in the connection URI.</span></span> <span data-ttu-id="f1142-131">使用者名稱和密碼必須是出現在 連線 URI 當您將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="f1142-131">The user name and password must be present in the connection URI when you add a service endpoint to the service host.</span></span>  
  
-   <span data-ttu-id="f1142-132">**PollingId**查詢字串參數，在 連線 URI。</span><span class="sxs-lookup"><span data-stu-id="f1142-132">The **PollingId** query string parameter in the connection URI.</span></span> <span data-ttu-id="f1142-133">如果您想要變更 POLLINGSTMT 作業的命名空間，您必須設定此連接屬性在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="f1142-133">If you want to change the namespace of the POLLINGSTMT operation, you must set this connection property both at design-time and run-time.</span></span>  
  
 <span data-ttu-id="f1142-134">繫結屬性和連接參數用來設定輪詢的完整說明，請參閱[在 Oracle 資料庫配接器收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="f1142-134">For a complete description of the binding properties and connection parameters used to configure polling, see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="f1142-135">WCF 服務合約和類別</span><span class="sxs-lookup"><span data-stu-id="f1142-135">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="f1142-136">您可使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來建立 WCF 服務合約 （介面），並支援 POLLINGSTMT 作業的類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-136">You use either the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] or the ServiceModel Metadata Utility Tool (svcutil.exe) to create a WCF service contract (interface) and supporting classes for the POLLINGSTMT operation.</span></span>  
  
 <span data-ttu-id="f1142-137">當您連接到 Oracle 資料庫，這些工具，以產生服務合約 POLLINGSTMT 作業的其中一種：</span><span class="sxs-lookup"><span data-stu-id="f1142-137">When you connect to the Oracle database with either of these tools to generate a service contract for the POLLINGSTMT operation:</span></span>  
  
-   <span data-ttu-id="f1142-138">您必須指定**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-138">You must specify the **PollingStatement** binding property.</span></span> <span data-ttu-id="f1142-139">配接器會使用這個繫結屬性中的 SELECT 陳述式，以產生強型別結果集 POLLINGSTMT 作業所傳回正確的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f1142-139">The adapter uses the SELECT statement in this binding property to generate the correct metadata for the strongly-typed result set returned by the POLLINGSTMT operation.</span></span>  
  
-   <span data-ttu-id="f1142-140">您可以選擇性地在 連線 URI 中指定 PollingId 參數。</span><span class="sxs-lookup"><span data-stu-id="f1142-140">You can optionally specify a PollingId parameter in the connection URI.</span></span> <span data-ttu-id="f1142-141">配接器會使用這個參數來產生 POLLINGSTMT 作業的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f1142-141">The adapter uses this parameter to generate the namespace for the POLLINGSTMT operation.</span></span>  
  
 <span data-ttu-id="f1142-142">在下列範例中：</span><span class="sxs-lookup"><span data-stu-id="f1142-142">In the following examples:</span></span>  
  
-   <span data-ttu-id="f1142-143">**PollingStatement**設為 「 選取 \* 從 ACCOUNTACTIVITY 的更新 」。</span><span class="sxs-lookup"><span data-stu-id="f1142-143">**PollingStatement** is set to "SELECT \* FROM ACCOUNTACTIVITY FOR UPDATE".</span></span>  
  
-   <span data-ttu-id="f1142-144">**PollingId**設為"AcctActivity"。</span><span class="sxs-lookup"><span data-stu-id="f1142-144">**PollingId** is set to "AcctActivity".</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="f1142-145">WCF 服務合約 （介面）</span><span class="sxs-lookup"><span data-stu-id="f1142-145">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="f1142-146">下列程式碼顯示產生 POLLINGSTMT 作業的 WCF 服務合約 （介面）。</span><span class="sxs-lookup"><span data-stu-id="f1142-146">The following code shows the WCF service contract (interface) generated for the POLLINGSTMT operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="POLLINGSTMT_OperationGroup")]  
public interface POLLINGSTMT_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)  
    // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT")]  
    void POLLINGSTMT(POLLINGSTMT request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="f1142-147">訊息合約</span><span class="sxs-lookup"><span data-stu-id="f1142-147">The Message Contracts</span></span>  
 <span data-ttu-id="f1142-148">訊息合約命名空間是 PollingId 參數連線 URI 中所修改。</span><span class="sxs-lookup"><span data-stu-id="f1142-148">The message contract namespace is modified by the PollingId parameter in the connection URI.</span></span> <span data-ttu-id="f1142-149">要求訊息會傳回一組的強型別的記錄。</span><span class="sxs-lookup"><span data-stu-id="f1142-149">The request message returns a set of strongly-typed records.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="POLLINGSTMT", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", IsWrapped=true)]  
public partial class POLLINGSTMT {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD;  
  
    public POLLINGSTMT() {  
    }  
  
    public POLLINGSTMT(microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD) {  
        this.POLLINGSTMTRECORD = POLLINGSTMTRECORD;  
    }  
}  
```  
  
### <a name="the-data-contract-namespace"></a><span data-ttu-id="f1142-150">資料合約命名空間</span><span class="sxs-lookup"><span data-stu-id="f1142-150">The Data Contract Namespace</span></span>  
 <span data-ttu-id="f1142-151">資料合約是服務和用戶端會以抽象方式描述要交換資料之間的正式合約。</span><span class="sxs-lookup"><span data-stu-id="f1142-151">A data contract is a formal agreement between a service and a client that abstractly describes the data to be exchanged.</span></span> <span data-ttu-id="f1142-152">也就是說，才能進行通訊，用戶端和服務不必共用相同的類型，只有相同的資料合約。</span><span class="sxs-lookup"><span data-stu-id="f1142-152">That is, in order to communicate, the client and the service do not have to share the same types, only the same data contracts.</span></span>  
  
 <span data-ttu-id="f1142-153">發生資料變更的訊息，資料合約命名空間也會修改 PollingId 參數 （如果有指定） 中的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="f1142-153">In case of data change messages, the data contract namespace is also modified by the PollingId parameter (if specified) in the connection URI.</span></span> <span data-ttu-id="f1142-154">資料合約是由表示強型別中的記錄查詢結果集的類別組成。</span><span class="sxs-lookup"><span data-stu-id="f1142-154">The data contract is composed of a class that represents a strongly-typed record in the query result set.</span></span> <span data-ttu-id="f1142-155">在此範例中，會省略類別定義的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="f1142-155">The details of the class definition are omitted in this example.</span></span> <span data-ttu-id="f1142-156">此類別包含代表結果集中的資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-156">The class contains properties that represent the columns in the result set.</span></span>  
  
 <span data-ttu-id="f1142-157">在下列範例中，會使用 PollingId"AcctActivity"。</span><span class="sxs-lookup"><span data-stu-id="f1142-157">In the following example, the PollingId “AcctActivity” is used.</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity {  
    using System.Runtime.Serialization;  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute(Name="POLLINGSTMTRECORD", Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity")]  
    public partial class POLLINGSTMTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
     }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="f1142-158">WCF 服務類別</span><span class="sxs-lookup"><span data-stu-id="f1142-158">WCF Service Class</span></span>  
 <span data-ttu-id="f1142-159">[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]也會產生虛設常式實作的服務合約 （介面） 的 WCF 服務類別的檔案。</span><span class="sxs-lookup"><span data-stu-id="f1142-159">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="f1142-160">檔案的名稱是 OracleDBBindingService.cs。</span><span class="sxs-lookup"><span data-stu-id="f1142-160">The name of the file is OracleDBBindingService.cs.</span></span> <span data-ttu-id="f1142-161">您可以插入的邏輯來處理 POLLINGSTMT 作業直接將這個類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-161">You can insert the logic to process the POLLINGSTMT operation directly into this class.</span></span> <span data-ttu-id="f1142-162">如果您使用 svcutil.exe 來產生服務合約介面時，您必須自行實作這個類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-162">If you use svcutil.exe to generate the service contract interface, you must implement this class yourself.</span></span> <span data-ttu-id="f1142-163">下列程式碼將示範所產生的 WCF 服務類別[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f1142-163">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : POLLINGSTMT_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)   
        // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void POLLINGSTMT(POLLINGSTMT request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-the-pollingstmt-operation"></a><span data-ttu-id="f1142-164">接收 POLLINGSTMT 作業</span><span class="sxs-lookup"><span data-stu-id="f1142-164">Receiving the POLLINGSTMT Operation</span></span>  
  
#### <a name="to-receive-polling-data-from-the-oracle-database-adapter"></a><span data-ttu-id="f1142-165">接收來自 Oracle 資料庫配接器輪詢資料</span><span class="sxs-lookup"><span data-stu-id="f1142-165">To receive polling data from the Oracle Database adapter</span></span>  
  
1.  <span data-ttu-id="f1142-166">使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]或 svcutil.exe 產生 WCF 服務合約 （介面），並針對 POLLINGSTMT 作業的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-166">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or svcutil.exe to generate a WCF service contract (interface) and helper classes for the POLLINGSTMT operation.</span></span> <span data-ttu-id="f1142-167">如需詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="f1142-167">For more information, see [Generate a WCF client or a WCF service contract for Oracle Database solution artifacts](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md).</span></span> <span data-ttu-id="f1142-168">最少，您必須設定**PollingStatement**繫結屬性，當您連接到配接器。</span><span class="sxs-lookup"><span data-stu-id="f1142-168">At a minimum, you must set the **PollingStatement** binding property when you connect to the adapter.</span></span> <span data-ttu-id="f1142-169">您可以選擇性地在 連線 URI 中指定 PollingId 參數。</span><span class="sxs-lookup"><span data-stu-id="f1142-169">You can optionally specify a PollingId parameter in the connection URI.</span></span> <span data-ttu-id="f1142-170">如果您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，您應該設定的繫結參數的所有必要組態。</span><span class="sxs-lookup"><span data-stu-id="f1142-170">If you are using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], you should set all of the binding parameters necessary for your configuration.</span></span> <span data-ttu-id="f1142-171">這可確保它們已正確設定在產生的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="f1142-171">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
2.  <span data-ttu-id="f1142-172">實作 WCF 服務，從步驟 1 中所產生的介面和協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-172">Implement a WCF service from the interface and helper classes generated in step 1.</span></span> <span data-ttu-id="f1142-173">這個類別的 POLLINGSTMT 方法可以擲回例外狀況處理的資料，從 POLLINGSTMT 作業; 接收遇到錯誤時中止輪詢交易，否則此方法沒有傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="f1142-173">The POLLINGSTMT method of this class can throw an exception to abort the polling transaction, if an error is encountered processing the data received from the POLLINGSTMT operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="f1142-174">您必須屬性 WCF 服務類別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f1142-174">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
    1.  <span data-ttu-id="f1142-175">如果您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生介面，您可以實作您直接在邏輯**POLLINGSTMT**方法在產生**OracleDBBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-175">If you used the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate the interface, you can implement your logic directly in the **POLLINGSTMT** method in the generated **OracleDBBindingService** class.</span></span> <span data-ttu-id="f1142-176">這個類別可以 OracleDBBindingService.cs 中找到。</span><span class="sxs-lookup"><span data-stu-id="f1142-176">This class can be found in OracleDBBindingService.cs.</span></span> <span data-ttu-id="f1142-177">這段程式碼，在此範例中的子類別**OracleDBBindingService**類別。</span><span class="sxs-lookup"><span data-stu-id="f1142-177">This code in this example sub-classes the **OracleDBBindingService** class.</span></span>  
  
        ```  
        [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
        public class PollingStmtService : OracleDBBindingService  
        {  
            public override void POLLINGSTMT(POLLINGSTMT request)  
            {  
                Console.WriteLine("\nNew Polling Records Received");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                        request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                        request.POLLINGSTMTRECORD[i].AMOUNT,  
                                        request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                        request.POLLINGSTMTRECORD[i].DESCRIPTION);  
                }  
            }  
        }  
        ```  
  
    2.  <span data-ttu-id="f1142-178">如果您使用 svcutil.exe 來產生介面時，您必須建立 WCF 服務的實作介面並實作您的邏輯中**POLLINGSTMT**這個類別的方法。</span><span class="sxs-lookup"><span data-stu-id="f1142-178">If you used svcutil.exe to generate the interface, you must create a WCF service that implements the interface and implement your logic in the **POLLINGSTMT** method of this class.</span></span>  
  
3.  <span data-ttu-id="f1142-179">建立在步驟 2 中建立的 WCF 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f1142-179">Create an instance of the WCF service created in step 2.</span></span>  
  
    ```  
    // create service instance  
    PollingStmtService pollingInstance = new PollingStmtService();  
    ```  
  
4.  <span data-ttu-id="f1142-180">建立的執行個體**system.servicemodel.servicehost 內**使用 WCF 服務和基底的連線 URI。</span><span class="sxs-lookup"><span data-stu-id="f1142-180">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="f1142-181">基底的連線 URI 不能包含 userinfoparams 或 query_string。</span><span class="sxs-lookup"><span data-stu-id="f1142-181">The base connection URI cannot contain userinfoparams or a query_string.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracledb://Adapter") };  
    ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
    ```  
  
5.  <span data-ttu-id="f1142-182">建立**OracleDBBinding**和設定輪詢作業設定其繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="f1142-182">Create an **OracleDBBinding** and configure the polling operation by setting its binding properties.</span></span> <span data-ttu-id="f1142-183">您可以在程式碼中明確或是宣告式組態。</span><span class="sxs-lookup"><span data-stu-id="f1142-183">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="f1142-184">最少，您必須指定輪詢陳述式和輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="f1142-184">At a minimum, you must specify the polling statement and polling interval.</span></span> <span data-ttu-id="f1142-185">在此範例中，您指定的認證做為 URI 的一部分，您也必須設定**AcceptCredentialsInUri**至**true**。</span><span class="sxs-lookup"><span data-stu-id="f1142-185">In this example, you specify the credentials as part of the URI so you must also set the **AcceptCredentialsInUri** to **true**.</span></span>  
  
    ```  
    // Create and configure a binding for the service endpoint. NOTE: binding  
    // parameters are set here for clarity, but these are already set in the  
    // the generated configuration file  
    OracleDBBinding binding = new OracleDBBinding();  
  
    // The credentials are included in the connection URI, so set this property to true  
    binding.AcceptCredentialsInUri = true;  
  
    // Same as statement specified in Configure Adapter dialog box  
    binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
    // Be sure to set the interval long enough to complete processing before  
    // the next poll  
    binding.PollingInterval = 15;  
    // Polling is transactional; be sure to set an adequate isolation level   
    // for your environment  
    binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
    ```  
  
6.  <span data-ttu-id="f1142-186">將服務端點加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="f1142-186">Add a service endpoint to the service host.</span></span> <span data-ttu-id="f1142-187">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="f1142-187">To do this:</span></span>  
  
    -   <span data-ttu-id="f1142-188">使用步驟 5 中建立的繫結。</span><span class="sxs-lookup"><span data-stu-id="f1142-188">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="f1142-189">指定連線 URI，其中包含認證並在必要時，PollingId。</span><span class="sxs-lookup"><span data-stu-id="f1142-189">Specify a connection URI that contains credentials and, if needed, a PollingId.</span></span>  
  
    -   <span data-ttu-id="f1142-190">為 「 POLLINGSTMT_OperationGroup"指定的合約。</span><span class="sxs-lookup"><span data-stu-id="f1142-190">Specify the contract as "POLLINGSTMT_OperationGroup".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
    Uri serviceUri = new Uri("oracledb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
    srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
    ```  
  
7.  <span data-ttu-id="f1142-191">若要收到輪詢資料，請開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="f1142-191">To receive polling data, open the service host.</span></span> <span data-ttu-id="f1142-192">每當查詢會傳回結果集時，配接器會傳回資料。</span><span class="sxs-lookup"><span data-stu-id="f1142-192">The adapter will return data whenever the query returns a result set.</span></span>  
  
    ```  
    // Open the service host to begin polling  
    srvHost.Open();  
    ```  
  
8.  <span data-ttu-id="f1142-193">若要終止輪詢，關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="f1142-193">To terminate polling, close the service host.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f1142-194">配接器將會繼續輪詢直到關閉服務主機。</span><span class="sxs-lookup"><span data-stu-id="f1142-194">The adapter will continue to poll until the service host is closed.</span></span>  
  
    ```  
    srvHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="f1142-195">範例</span><span class="sxs-lookup"><span data-stu-id="f1142-195">Example</span></span>  
 <span data-ttu-id="f1142-196">下列範例顯示針對/SCOTT/ACCOUNTACTIVITY 資料表執行在有輪詢查詢。</span><span class="sxs-lookup"><span data-stu-id="f1142-196">The following example shows a polling query that executes against the /SCOTT/ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="f1142-197">後輪詢陳述式會叫用會處理的記錄移至另一個資料表 /SCOTT/ACCOUNTHISTORY Oracle 函式。</span><span class="sxs-lookup"><span data-stu-id="f1142-197">The post-poll statement invokes an Oracle function that moves the processed records to another table /SCOTT/ACCOUNTHISTORY.</span></span> <span data-ttu-id="f1142-198">POLLINGSTMT 作業的命名空間是由 PollingId 將參數設定為"AccountActivity 」 連線 URI 中進行修改。</span><span class="sxs-lookup"><span data-stu-id="f1142-198">The namespace of the POLLINGSTMT operation is modified by setting the PollingId parameter to "AccountActivity" in the connection URI.</span></span> <span data-ttu-id="f1142-199">在此範例中，WCF 服務 POLLINGSTMT 作業由分為子類別產生**OracleDBBindingService**類別; 不過，您可以直接在產生的類別中實作您的邏輯。</span><span class="sxs-lookup"><span data-stu-id="f1142-199">In this example, the WCF service for the POLLINGSTMT operation is created by sub-classing the generated **OracleDBBindingService** class; however, you can implement your logic directly in the generated class.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add these three references to use the Oracle adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
using microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity;  
using OracleDBBindingNamespace;  
  
namespace OraclePollingSM  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingStmtService : OracleDBBindingService  
    {  
        public override void POLLINGSTMT(POLLINGSTMT request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
            for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                    request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                    request.POLLINGSTMTRECORD[i].AMOUNT,  
                                    request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                    request.POLLINGSTMTRECORD[i].DESCRIPTION);  
  
            }  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
         }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost srvHost = null;  
  
            // This URI is used to specify the address for the ServiceEndpoint  
            // It must contain credentials and the PollingId (if any) that was used to generate  
            // the WCF service callback interface  
            Uri serviceUri = new Uri("OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
  
            // This URI is used to initialize the ServiceHost. It cannot contain  
            // userinfoparms (credentials) or a query_string (PollingId); otherwise,  
            // an exception is thrown when the ServiceHost is initialized.  
            Uri[] baseUri = new Uri[] { new Uri("OracleDb://Adapter") };  
  
            Console.WriteLine("Sample started, initializing service host -- please wait");  
  
            // create an instanc of the WCF service callback class  
            PollingStmtService pollingInstance = new PollingStmtService();  
  
            try  
            {  
                // Create a ServiceHost with the service callback instance and a base URI (address)  
                srvHost = new ServiceHost(pollingInstance, baseUri);  
  
                // Create and configure a binding for the service endpoint. Note: binding  
                // parameters are set here for clarity but these are already set in the  
                // generated configuration file  
                //  
                // The following properties are set  
                //    AcceptCredentialsInUri (true) to enable credentials in the connection URI for AddServiceEndpoint  
                //    PollingStatement  
                //    PostPollStatement calls PROCESS_ACTIVITY on Oracle. This procedure moves the queried records to  
                //                      the ACCOUNTHISTORY table  
                //    PollingInterval (15 seconds)  
                //    TransactionIsolationLevel   
  
                OracleDBBinding binding = new OracleDBBinding();  
  
                // The Credentials are included in the Connection Uri so set this property true  
                binding.AcceptCredentialsInUri = true;  
  
                // Same as statement specified in Configure Adapter dialog box  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Be sure to set the interval long enough to complete processing before  
                // the next poll  
                binding.PollingInterval = 15;  
  
                // Polling is transactional, be sure to set an adequate isolation level   
                // for your environment  
                binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
  
                // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
                srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
  
                Console.WriteLine("Opening the service host");  
                // Open the service host to begin polling  
                srvHost.Open();  
  
                // Wait to receive request  
                Console.WriteLine("\nPolling started. Returned records will be written to the console.");  
                Console.WriteLine("Hit <RETURN> to stop polling");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an Oracle Error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (srvHost.State == CommunicationState.Opened)  
                    srvHost.Close();  
                else  
                    srvHost.Abort();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1142-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1142-200">See Also</span></span>  
 [<span data-ttu-id="f1142-201">開發使用 WCF 服務模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="f1142-201">Develop Oracle Database applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)
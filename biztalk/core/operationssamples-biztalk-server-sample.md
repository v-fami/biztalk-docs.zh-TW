---
title: OperationsSamples （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c9e3f3e-a570-4edd-aa2e-3f8e2e37c8a0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e42b17f19791eef9bd3f1b5d7d4554f61f08356
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010247"
---
# <a name="operationssamples-biztalk-server-sample"></a>OperationsSamples (BizTalk Server 範例)
OperationsSamples 範例示範如何利用 Operations 物件模型來執行操作活動。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例示範下列作業：  
  
-   如何使用追蹤設定檔，在協調流程加上活動註解。  
  
-   如何使用 BAM 追蹤資料庫尋找活動識別碼，並接著使用此識別碼尋找相關的協調流程執行個體。  
  
-   如何尋找及使用訊息流程透過**MessageFlow**類別和其他作業物件模型類別和應用程式開發介面。  
  
-   如何存取連接埠、 訊息，以及其他執行個體所使用的類別衍生自**執行個體**類別。  
  
 此範例包含許多可用來支援上述作業的協助程式類別和方法。 下節內容將討論這些範例程式碼和其他程式碼的重點。  
  
## <a name="how-this-sample-is-designed-and-why"></a>此範例的設計方式和原因  
 本範例是設計用來示範 Operations 物件模型中的幾個重要類別和方法，並會示範如何查詢公開的 BAM 追蹤資料庫。  
  
 Operations 物件模型所包含的類別，可在 BizTalk Server 內操作訊息和其他執行個體。  
  
### <a name="using-a-bam-activity-id"></a>使用 BAM 活動識別碼  
 本範例會示範如何與 BAM 互動，以及如何使用追蹤資料庫的公開檢視，以便透過使用商務資料來找出 MessageBox 中的即時訊息。 此範例會擷取對應於訂單編號的協調流程識別碼，完成此作業。 為了成功完成這項工作，此範例必須執行下列動作：  
  
1.  使用商務資料 (訂單號碼) 尋找活動識別碼。 這個步驟會將商務資料對應到可用來尋找其他資訊的內部識別碼。  
  
2.  擷取與活動識別碼相關的 BAM 參考。  
  
3.  尋找類型為 "BizTalkService" 且參考至特定協調流程的參考。 如果有找到符合的項目，便傳回其執行個體識別碼。  
  
 這項功能由**BAMWebService.GetOrchestrationID**靜態方法和相關聯的 helper 方法，包括 BamManagementService.cs 原始程式檔中的類別和方法。  
  
### <a name="suspending-terminating-and-resuming-an-instance"></a>擱置、終止與繼續執行個體  
 範例程式中包含**Samples.OperateOnInstance**接受作業和執行個體的識別碼，並執行指定的作業的執行個體上的方法。 有效的作業會由**InstanceOperation**列舉型別，並包含 Suspend、 Terminate 和 Resume。 這些作業會直接對應到 BizTalkOperations 類別的方法-**SuspendInstance**， **TerminateInstance**，和**ResumeInstance**。  
  
 請注意，此方法會處理 ArgumentException 和 SqlException 等例外狀況。 在使用 Operations 物件模型中的類別和方法時，您必須謹慎地預先考慮到包括 SqlException 的例外狀況。  
  
> [!NOTE]
>  許多 Operations 方法必須要存取該資料庫。 您應該預先考慮到這些方法所擲回的例外狀況，並適當進行處理。  
  
### <a name="retrieving-all-live-messages"></a>擷取所有即時訊息  
 Operations 物件模型可以讓您直接逐一查看所有可用的即時訊息，如下列程式碼片段所示：  
  
```  
BizTalkOperations _operations = new BizTalkOperations()  
IEnumerable messages = _operations.GetMessages();  
foreach (BizTalkMessage msg in messages)  
…  
```  
  
 OperationsSamples 程式會進一步示範如何存取每個訊息的相關資訊，包括訊息識別碼、訊息類型，以及訊息部份的數目和類型。 您可以針對必須逐一查看 BizTalk Server 中的多數或全部即時訊息的情況，修改並使用此程式碼。  
  
> [!NOTE]
>  可用的訊息數目可能是成千上百個。 若是掃描整個清單，可能會對效能造成不良的影響。  
  
## <a name="where-to-find-this-sample"></a>可在何處找到此範例  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\OperationsOM\OperationsSamples\  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|BamManagementService.cs|BAM Web 服務的 Web Proxy 類別。|  
|Cleanup.bat|移除範例協調流程，並將 HelloWorld 範例還原成原始狀態。|  
|HelloOrchestration.btt|用來將 BizTalk 事件來源對應到 BAM 目標活動的追蹤設定檔。|  
|HelloOrchestration.xls|BAM 定義樣式表。|  
|OperationsSamples.cs|C# 原始程式檔，其中包含示範 Operations 物件模型各方面的程式碼。|  
|OperationsSamples.csproj、OperationsSamples.sln、AssemblyInfo.cs|此範例的專案、解決方案和組件資訊檔案。|  
|Setup.bat|這個檔案是用來建置及初始化這個範例，其方法是修改 HelloWorld 協調流程範例。 此檔案會安裝範例協調流程、部署 BAM 活動定義和追蹤設定檔編輯器檔案、設定連接埠，並將範例檔放在接收位置中。|  
  
## <a name="how-to-use-this-sample"></a>如何使用此範例  
 使用此範例，瞭解 Operations 作業物件模型的可用功能。 修改現有常式尋找訊息，以便採取不同方式來使用訊息；或是加入新程式碼，以便複寫 [BizTalk Server 管理] 主控台中的 [群組中樞] 部分。  
  
 您也可以考慮執行下列工作：  
  
-   撰寫應用程式，將最常使用的 [群組中樞] 子集複寫到自訂的應用程式。  
  
-   撰寫自訂的佈建應用程式，以便建立連接埠，並透過連接埠傳送測試訊息給新交易夥伴。  
  
-   將範例程式修改為命令列公用程式，以便在螢幕、XML 檔案或文字報告中提供單一訂單或各種訂單的相關資訊。  
  
## <a name="installing-sample-support-files"></a>安裝範例支援檔案  
 本節將引導您完成安裝及執行範例的必要程序。  
  
> [!NOTE]
>  安裝及執行此範例之前，您必須確定 BAM 已安裝且運作。 若未安裝 BAM，此範例將無法執行。  
  
#### <a name="to-compile-and-install-the-support-files-for-this-sample"></a>若要編譯及安裝此範例的支援檔案  
  
1.  在命令視窗中，瀏覽至下列資料夾：  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
2.  執行 Setup.bat，這會執行下列動作：  
  
    -   建立傳送和接收目錄  
  
    -   建立及啟動傳送埠和接收埠  
  
    -   編譯及部署 `<Samples Path>`\Orchestrations\HelloWorld 資料夾中的 HelloWorld 協調流程。  
  
    -   修改 HelloWorld 協調流程的公開金鑰 Token  
  
    -   部署 BAM 活動定義和追蹤設定檔編輯器檔案  
  
    -   重新命名此 out 目錄  
  
    > [!NOTE]
    >  若要中止安裝，請在第一個「請按任何一個鍵繼續」提示時按 CTRL+C。 這樣就可停止指令碼，並使 HelloWorld 範例保留在原始狀態。 若是在第二個 (也是最後一個) 提示中按 CTRL+C，並不會停止安裝。 在此狀況下，請執行 Cleanup.bat 以解除安裝 OperationsOM 範例並還原 HelloWorld 範例。  
  
## <a name="running-this-sample"></a>執行此範例  
 使用下列程序執行 OperationsOM 範例。  
  
#### <a name="to-compile-and-run-the-sample"></a>若要編譯及執行範例  
  
1.  按一下**啟動**，選取**所有程式**，選取**Microsoft BizTalk Server**，然後選取**BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**平台設定**，然後展開  **主控件執行個體**。  
  
3.  以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 **重新啟動**。  
  
    > [!NOTE]
    >  如果在設定產品之後尚未重新啟動該主控件執行個體，這時您可能需要重新啟動 BizTalkServerApplication 主控件執行個體，以設定 BAM 正確的工作資料庫。  
  
4.  從 Windows 檔案總管瀏覽至下列資料夾：  
  
     `<Samples Path>\Admin\OperationsOM\OperationSamples`  
  
5.  按兩下 **[operationsom.sln]** 載入 Visual Studio 專案檔。  
  
6.  按 F5 執行範例。  
  
     -或-  
  
     在**建置**功能表上，按一下 **重建方案**。 當組建完成時，使用 Windows 檔案總管瀏覽至`<Samples Path>\Admin\OperationsOM\OperationSamples\bin\Debug,`，然後按兩下  **OperationsSamples.exe**。  
  
## <a name="classes-or-methods-used-in-this-sample"></a>在此範例中使用的類別或方法  
 [Microsoft.BizTalk.Operations.BizTalkOperations](http://msdn.microsoft.com/library/microsoft.biztalk.operations.biztalkoperations.aspx)&#124;[Microsoft.BizTalk.Operations.MessageFlow](http://msdn.microsoft.com/library/microsoft.biztalk.operations.messageflow.aspx)&#124;[Microsoft.BizTalk.Operations.SendPortInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.sendportinstance.aspx)&#124;[Microsoft.BizTalk.Operations.RoutingFailureInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.routingfailureinstance.aspx)&#124;[Microsoft.BizTalk.Operations.OrchestrationInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.orchestrationinstance.aspx)&#124;[Microsoft.BizTalk.Operations.MSMQtInstance](http://msdn.microsoft.com/library/microsoft.biztalk.operations.msmqtinstance.aspx)&#124;[Microsoft.BizTalk.Operations.TrackedServiceInstance](http://msdn.microsoft.com/library/Microsoft.BizTalk.Operations.TrackedServiceInstance.aspx)  
  
## <a name="see-also"></a>請參閱  
 [Admin-OperationsOM (BizTalk Server Samples 資料夾)](../core/admin-operationsom-biztalk-server-samples-folder.md)
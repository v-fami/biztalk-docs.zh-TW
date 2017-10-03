---
title: "如何設定用於攔截的 Workflow Foundation 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c82e83f-9dbd-4325-9f30-778eba892296
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad184ce4b0ef619361f44f6eb1ee54a2354f5148
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-workflow-foundation-application-for-interception"></a>如何設定用於攔截的 Workflow Foundation 應用程式
您必須安裝 BAM 攔截器軟體，並設定應用程式使用 [!INCLUDE[firstref_btsWinWorkflowFoundation](../includes/firstref-btswinworkflowfoundation-md.md)] 攔截器服務，才能開始收集 BAM 活動資料。 假設您已成功安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及其相依性，而且至少已建立一個 BizTalk 群組。  
  
## <a name="installing-the-bam-eventing-software"></a>安裝 BAM-Eventing 軟體  
 您必須使用 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 安裝程式安裝 BAM-Eventing 軟體，才能將 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式設定為使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BAM 攔截器。 如需有關安裝 Bam-eventing 軟體及註冊效能計數器的詳細資訊，請參閱[安裝 Bam-eventing 軟體](../core/installing-the-bam-eventing-software.md)。  
  
## <a name="configuring-a-windows-workflow-foundation-application-for-tracking"></a>設定用於追蹤的 Windows Workflow Foundation 應用程式  
 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式可以開始寫入 BAM 事件資訊前，必須先完成四項工作：  
  
-   必須利用建立觀察模型[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BAM 工具，並接著使用 BAM 管理員命令列工具 (bm.exe) 部署。  
  
-   必須使用 BAM 管理員命令列工具 (bm.exe) 建立及部署攔截器組態檔。  
  
-   執行主應用程式的使用者必須屬於適當 BAM 活動事件寫入器 (bam_\<活動 > _EventWriter) 以啟用讀取攔截器組態資訊以及寫入 BAM 應用程式的 SQL Server 角色活動。  
  
-   App.config 檔案或應用程式本身必須經過修改，才能載入 BAM 追蹤服務並接著重新啟動應用程式。  
  
 唯有成功完成這些工作，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM 資料庫內才會開始出現事件。  
  
### <a name="deploying-an-observation-model"></a>部署觀察模型  
 您必須部署觀察模型，才能部署攔截器組態檔或擷取您應用程式中的 BAM 活動。  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a>若要使用 bm.exe 部署觀察模型  
  
1.  按一下**啟動**，然後按一下 **執行**開啟 Windows 命令提示字元。  
  
2.  型別**cmd**中**開啟**欄位，，然後按一下**確定**。  
  
3.  使用變更目錄命令移至內含要部署之觀察模型的目錄。 例如， **cd c:\businessprocess\Orders**。  
  
4.  使用 bm.exe 部署觀察模型：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\BM.exe deploy-all-definitionfile-definitionfile:\<*definitionfile.xml*>  
  
     請確定您取代\< *definitionfile.xml*> 具有您想要部署的觀察檔案名稱。 如需其他選項，請參閱[攔截器管理命令](../core/interceptor-management-commands.md)。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  型別**結束**，然後按 ENTER 關閉命令提示字元。  
  
### <a name="deploying-an-interceptor-configuration-file"></a>部署攔截器組態檔  
 您必須部署攔截器組態檔，應用程式才能擷取 BAM 活動。  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a>若要使用 bm.exe 部署攔截器組態檔  
  
1.  按一下**啟動**，然後按一下 **執行**開啟 Windows 命令提示字元。  
  
2.  型別**cmd**中**開啟**欄位，，然後按一下**確定**。  
  
3.  使用變更目錄命令移至內含要部署之攔截器組態檔的目錄。 例如， **cd c:\businessprocess\Orders**。  
  
4.  使用 bm.exe 部署攔截器組態檔：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\BM.exe 部署攔截器-filename:\<*icfile.xml*>  
  
     請確定您取代\< *icfile.xml*> 您想要部署攔截器組態檔的名稱。  
  
    > [!NOTE]
    >  您可以使用**-Force: True**覆寫現有的事件來源的攔截器組態檔中的相同名稱的旗標。 如果您這樣做，請務必先備份使用現有的組態**get 攔截器**命令。 使用 -Force:True 旗標可能會刪除任何參考要覆寫之事件來源的攔截器組態。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  型別**結束**，然後按 ENTER 關閉命令提示字元。  
  
 若您已經部署 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式，在下一個輪詢間隔前，不會載入新組態。 然而，您若設定並重新啟動應用程式，就會立即收取組態。  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a>加入使用者至適合的 BAM 活動角色  
 BAM 攔截器架構會讓每個活動使用一個 SQL Server 角色，控制活動和組態資訊的存取。 您必須將執行 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式的使用者帳戶，加入至 BAM 主要匯入資料庫內的適當 BAM 活動角色。  
  
### <a name="configuring-the-application-to-load-the-bam-tracking-service"></a>設定應用程式以載入 BAM 追蹤服務  
 在 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式載入 BAM 追蹤服務的實例有三種：  
  
-   若 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式已經使用 WorkflowRuntime 載入 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 組態區段，則您可以將 BAM 追蹤服務資訊加入至現有區段。  
  
-   若 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式並未使用 WorkflowRuntime 載入 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 組態區段，則您必須新增程式碼才能從應用程式組態檔載入自訂區段。 您必須建立區段，並在該區段加入 BAM 追蹤服務資訊。  
  
-   若您想選擇以硬式編碼的方式寫入組態，可以使用 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] API 以程式設計的方式載入追蹤服務 (無須組態檔)，或從自訂來源載入組態。  
  
 設定 [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 應用程式時，請注意下列考量：  
  
-   [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 攔截器每一個 WorkflowRuntime 只支援一個 BamTrackingService。  
  
-   [!INCLUDE[nextref_btsWinWorkflowFoundation](../includes/nextref-btswinworkflowfoundation-md.md)] 攔截器的每個應用程式網域支援多個 BamTrackingService 執行個體。  
  
    -   N 個 WorkflowRuntime 就支援 N 個 BamTrackingService。  
  
-   若同一個應用程式網域中，不同的 BamTrackingService 執行個體使用不同的連線字串，攔截器就會引發例外狀況。  
  
-   攔截器會從第一個啟動的 BamTrackingService 執行個體取得 IC 輪詢間隔值。  
  
-   應用程式網域中的最後一個 BamTrackingService 停止時，攔截器就會停止 IC 輪詢執行緒。  
  
 如需 WorkflowRuntime 和載入組態資訊的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=83314](http://go.microsoft.com/fwlink/?LinkId=83314)。  
  
##### <a name="to-configure-the-appconfig-file-for-the-bam-tracking-service"></a>若要設定 BAM 追蹤服務的 App.config 檔案  
  
1.  開啟與應用程式關聯的 App.config 檔案。 使用 Notepad.exe 或其他文字編輯器開啟即可。  
  
2.  將下列組態資訊插入 App.config 檔案以新增 BAM 追蹤服務。 請定位該資訊，讓它成為 `configuration` 元素的子系。  
  
    > [!NOTE]
    >  項目應該對應至使用 WorkflowRuntime 類別時，應用程式程式碼所使用的名稱。  
  
    ```  
    <!-- The element name must match the one expected by WorkflowRuntime in your WF application -->  
    <WorkflowServiceContainer>  
      <Services>  
        <add type="Microsoft.BizTalk.Bam.Interceptors.Workflow.BamTrackingService, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"  
       ConnectionString="Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"   
          PollingIntervalSec="5"/>  
        </Services>  
    </WorkflowServiceContainer>  
    ```  
  
3.  修改**ConnectionString**屬性，以符合您的環境。  
  
4.  重新啟動您的應用程式。  
  
##### <a name="to-modify-your-application-to-load-a-custom-configuration-section"></a>若要修改應用程式以載入自訂組態區段  
  
1.  在 Visual Studio 中開啟 Windows Workflow Foundation 專案。  
  
2.  將具有適合之參數的新 BamTrackingService 執行個體，加入至應用程式的 WorkflowRuntime 執行個體：  
  
    ```  
    // !! Replace "WorkflowServiceContainer" with the section name  
    // you used in your App.config file.  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime("WorkflowServiceContainer");  
    ```  
  
3.  重新編譯並部署修改後的應用程式。  
  
##### <a name="to-modify-your-application-to-programmatically-load-the-bam-tracking-service"></a>若要修改應用程式以透過程式設計的方式載入 BAM 追蹤服務  
  
1.  在 Visual Studio 中開啟 Windows Workflow Foundation 專案。  
  
2.  將具有適合之參數的新 BamTrackingService 執行個體，加入至應用程式的 WorkflowRuntime 執行個體：  
  
    ```  
    string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport"  
    int pollingInterval = 5;  
    WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
    workflowRuntime.AddService(new BamTrackingService(connectionString, pollingInterval));  
    ```  
  
     您可根據特定環境新增或移除參數。  
  
3.  重新編譯並部署修改後的應用程式。
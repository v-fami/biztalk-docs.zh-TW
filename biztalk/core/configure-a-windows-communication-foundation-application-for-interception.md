---
title: 如何設定用於攔截的 Windows Communication Foundation 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37f2ccde-aa79-470a-ac31-57e4168dc54a
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42f8328268b82a377bb6d73f3bd7305122a830c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969652"
---
# <a name="how-to-configure-a-windows-communication-foundation-application-for-interception"></a>如何設定用於攔截的 Windows Communication Foundation 應用程式
您必須安裝 BAM 攔截器軟體，並設定應用程式使用 BAM [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 攔截器服務，才能開始收集 BAM 活動資料。 假設您已成功安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 及其相依性，而且至少已建立一個 BizTalk 群組。  
  
## <a name="installing-the-bam-eventing-software"></a>安裝 BAM-Eventing 軟體  
 您必須使用 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 安裝程式安裝 BAM-Eventing 軟體，才能將 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式設定為使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的 BAM 攔截器。 如需有關安裝 Bam-eventing 軟體及註冊效能計數器的詳細資訊，請參閱[安裝 Bam-eventing 軟體](../core/installing-the-bam-eventing-software.md)。  
  
## <a name="configuring-a-wcf-application-for-tracking"></a>設定 WCF 應用程式進行追蹤  
 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式可以開始寫入 BAM 事件資訊前，必須先完成四項工作：  
  
-   必須使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM 工具建立觀察模型，接著使用「BAM 管理員」命令列工具 (bm.exe) 加以部署。  
  
-   必須使用「BAM 管理員」命令列工具 (bm.exe) 建立及部署攔截器組態檔。  
  
-   執行主應用程式的使用者必須屬於適當 BAM 活動事件寫入器 (bam_\<活動\>_EventWriter) 讓應用程式來讀取攔截器組態資訊和寫入 SQL Server 角色BAM 活動。  
  
-   伺服器和用戶端應用程式的 App.config 檔必須經過修改，才能載入 BAM 追蹤服務。 App.config 檔經過修改之後，必須重新啟動應用程式。  
  
 唯有成功完成這些工作，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BAM 資料庫內才會開始出現事件。  
  
### <a name="deploying-an-observation-model"></a>部署觀察模型  
 您必須部署觀察模型，才能部署攔截器組態檔或擷取您應用程式中的 BAM 活動。  
  
##### <a name="to-deploy-an-observation-model-by-using-bmexe"></a>若要使用 bm.exe 部署觀察模型  
  
1.  按一下**啟動**，然後按一下 **執行**開啟 Windows 命令提示字元。  
  
2.  型別**cmd**中**開啟**欄位，，然後按一下**確定**。  
  
3.  使用變更目錄命令移至內含要部署之觀察模型的目錄。 例如， **cd c:\businessprocess\Orders**。  
  
4.  使用 bm.exe 部署觀察模型：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm.exe deploy-all-definitionfile-Definitionfile:\<*definitionfile.xml*\>  
  
     請確定您取代\< *definitionfile.xml* \>您想要部署的觀察模型檔案的名稱。 如需其他選項，請參閱[攔截器管理命令](../core/interceptor-management-commands.md)。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  型別**結束**，然後按 enter 鍵關閉命令提示字元。  
  
### <a name="deploying-an-interceptor-configuration-file"></a>部署攔截器組態檔  
 您必須部署攔截器組態檔，應用程式才能擷取 BAM 活動。  
  
##### <a name="to-deploy-an-interceptor-configuration-file-by-using-bmexe"></a>若要使用 bm.exe 部署攔截器組態檔  
  
1.  按一下**啟動**，然後按一下 **執行**開啟 Windows 命令提示字元。  
  
2.  型別**cmd**中**開啟**欄位，，然後按一下**確定**。  
  
3.  使用變更目錄命令移至內含要部署之攔截器組態檔的目錄。 例如， **cd c:\businessprocess\Orders**。  
  
4.  使用 bm.exe 部署攔截器組態檔：  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking\bm.exe 部署攔截器-Filename:\<*icfile.xml*\>  
  
     請確定您取代\< *icfile.xml* \>您想要部署攔截器組態檔的名稱。  
  
    > [!NOTE]
    >  您可以使用 **-Force: True**覆寫現有的事件來源的攔截器組態檔中的相同名稱的旗標。 如果您這樣做，請務必先備份使用現有的組態**get 攔截器**命令。 使用 -Force:True 旗標可能會刪除任何參考要覆寫之事件來源的攔截器組態。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
5.  型別**結束**，然後按 enter 鍵關閉命令提示字元。  
  
 若您已經部署 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式，在下一個輪詢間隔前，不會載入新組態。 然而，您若設定並重新啟動應用程式，就會立即收取組態。  
  
### <a name="adding-the-user-to-the-appropriate-bam-activity-role"></a>加入使用者至適合的 BAM 活動角色  
 BAM 攔截器架構會讓每個活動使用一個 SQL Server 角色，控制活動和組態資訊的存取。 您必須將執行 WCF 應用程式的使用者帳戶，加入至 BAMPrimaryImport 資料庫內的適當 BAM 活動角色。  
  
### <a name="configuring-the-windows-communication-foundation-application-to-load-the-bam-tracking-service"></a>設定讓 Windows Communication Foundation 應用程式載入 BAM 追蹤服務  
 您可透過新增數行至伺服器或用戶端應用程式的 App.config 檔的方式，設定應用程式載入 BAM 追蹤服務。  
  
 若要在 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 伺服器或用戶端應用程式中設定 BAM 追蹤，您將需要修改 App.config 組態檔來加入額外的端點行為與行為延伸模組，以及新增行為組態屬性。 服務和用戶端範本的格式相似。  
  
 設定 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 應用程式時，請注意下列事項。 如果相同應用程式 (也就是相同的用戶端或服務) 的 App.config 中定義了多種 BAM 端點行為，則 BAM 將採取下列動作。  
  
-   如果連接字串不同，則 BAM 將引發例外狀況。  
  
-   如果只有輪詢間隔不同，則 BAM 將選取其中一種行為並繼續執行。 在設計階段無法判斷將選取哪一種行為。  
  
> [!NOTE]
>  如果連接字串相同 (表示參考同一部電腦)，則 BAM 處理將正常執行。  
  
 下列範例 App.config 範本是針對 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 伺服器應用程式所設定。 它會定義使用自訂行為 "bamEndpointBehavior" 的端點，且該自訂行為設定為使用 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 攔截器。  
  
```  
<system.serviceModel>  
  <services>  
    <service name="Service.CreditCardAuthorization">  
      <!-- The endpoint will use the "bamEndpointBehavior" -->   
      <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    </service>  
  </services>  
  <bindings>  
    <wsDualHttpBinding>  
      <binding name="wsDualHttpBinding_ICreditCardAuthorization" transactionFlow="true" />  
    </wsDualHttpBinding>  
  </bindings>  
  <behaviors>  
    <endpointBehaviors>  
      <!-- Define a new behavior named "bamEndpointBehavior" -->  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <extensions>  
    <behaviorExtensions>  
      <!-- Define a new enpoint behavior extension using WCF interceptor -->  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
  </extensions>  
</system.serviceModel>  
```  
  
 您將需要對此範本進行細部調整，才能在自己的 App.config 檔中使用。  
  
##### <a name="to-use-this-template-in-your-wcf-service-appconfig-file"></a>在您的 WCF 服務 App.config 檔中使用此範本  
  
1.  開啟與應用程式關聯的 App.config 檔案。 使用 Notepad.exe 或其他文字編輯器開啟即可。  
  
2.  使用下列 XML 新增 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] BamEndpointBehavior 行為延伸模組至 `extensions` 項目：  
  
    ```  
    <behaviorExtensions>  
      <add name="BamEndpointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
    </behaviorExtensions>  
    ```  
  
    > [!NOTE]
    >  行為延伸模組命名為 "BamEndpointBehaviorExtension"，並且可以視您的環境需要進行變更。  
  
3.  使用下列 XML 將使用新的行為延伸模組的新端點行為新增至`behaviors` 項目。 行為延伸模組會提供連接字串和以秒為單位的輪詢間隔。  
  
    ```  
    <endpointBehaviors>  
      <behavior name="bamEndpointBehavior">  
        <BamEndpointBehaviorExtension ConnectionString="Initial Catalog=BamPrimaryImport;Data Source=MyMachine;Integrated Security=SSPI;" InterceptorConfigurationPollingInterval="1500" />  
      </behavior>  
    </endpointBehaviors>  
    ```  
  
     請將 [資料來源] 取代為您環境中裝載 BamPrimaryImport 資料庫的電腦名稱。 配合您的環境變更輪詢間隔，數字越大，表示 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 攔截器偵測組態變更的時間間隔越長。 如果您已變更行為延伸模組的名稱，請使用該名稱取代 "BamEndpointBehaviorExtension"。  
  
    > [!NOTE]
    >  行為命名為 "bamEndpointBehavior"，並且可以視您的環境需要進行變更。  
  
    > [!NOTE]
    >  指定 `ConnectionString` 時，避免使用純文字的使用者名稱/密碼組合。 否則可能危害您的資料庫伺服器。  
  
    > [!NOTE]
    >  您必須指定大於或等於 5 (秒) 的 `PollingIntervalSec`。 如果您指定較小的值或略過 `PollingIntervalSec` 項目，則會發生錯誤而且將不會設定攔截。  
  
4.  新增 `behaviorConfiguration` 屬性至您將追蹤的端點，並且提供新行為的名稱：  
  
    ```  
    <endpoint address="http://localhost:8081/CreditCardService" contract="Service.ICreditCardAuthorization" name="CreditCardEndPoint" binding ="wsDualHttpBinding" bindingConfiguration="wsDualHttpBinding_ICreditCardAuthorization" behaviorConfiguration="bamEndpointBehavior"/>  
    ```  
  
    > [!NOTE]
    >  如果您使用不同的行為名稱，請提供該名稱。  
  
     您可以套用行為組態至多個端點。  
  
5.  儲存修改過的 App.config 檔，並且重新啟動應用程式。
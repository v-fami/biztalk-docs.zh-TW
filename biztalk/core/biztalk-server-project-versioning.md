---
title: "BizTalk Server 專案版本設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcdd5354-6335-4320-adbf-28ac934c9ce6
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1893509d569dc74bf8d6d28680026ebe90ba9149
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-project-versioning"></a>BizTalk Server 專案版本管理
在使用 [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 進行開發時，版本管理是由一組規則標準所規範，用來降低變更版本號碼的影響。 如何根據[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]應用程式或元件的部署、 相依性可以透過 XCOPY 安裝應用程式組態檔或其他處理[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]部署機制。 如下列章節所示，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將其他複雜性新增至版本管理與相依性上。  
  
## <a name="implications-of-changing-version-numbers"></a>變更版本號碼的影響  
 在 [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 開發階段，通常我們在產生組建時會將組件版本號碼更新為目前的組建編號。 然而，在開發 BizTalk 解決方案時，變更組件版本號碼有可能會將組件與透過其組件版本號碼來參考 DLL 的相依項目之間的關係中斷。 下表列出使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件版本號碼來參考其組件的項目，以及變更組件版本號碼所產生的影響。  
  
|實體|變更組件版本號碼所產生的影響|  
|------------|------------------------------------------------|  
|繫結檔案|變更組件版本號碼會導致任何參考組件的現有繫結檔案無法執行。 這是因為繫結檔案會透過包含版本號碼的屬性來參考組件。<br /><br /> 您可以使用「記事本」或其他編輯程式來更新繫結檔案中的版本資訊。 您也可以重新部署解決方案，然後使用 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台] 來重新產生繫結檔案。 最後，您可以使用指令碼，自動化部署與版本管理的作業。 如需有關部署的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。|  
|BAM 追蹤設定檔定義 (.btt) 檔案|變更組件版本號碼會導致任何現有的 BAM 追蹤設定檔定義檔案無法執行。 由於 BAM 追蹤檔為二進位檔案格式，您無法加以編輯，只能重新產生新的追蹤檔。 如果需要 BAM 追蹤設定檔，則您可能需要進行下列任一項動作：<br /><br /> 為避免常常更新版本號碼，在建置程序。<br />-建立 BAM 追蹤設定檔之前的版本號碼的穩定性而延遲。|  
|使用 Web 服務發佈精靈來發佈 Web 服務|當您使用 Web 服務發佈精靈來產生 ASP.NET Web 介面時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組件的組件版本即已包含在 ASP.NET 原始程式碼中。 組件版本號碼是在執行階段由 ASP.NET 介面的一部分**bodyTypeAssemblyQualifiedName** Web 服務作業的屬性。 如果版本號碼[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組件變更，而無須更新**bodyTypeAssemblyQualifiedName**屬性，則後續的 Web 服務作業將會拒絕的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。<br /><br /> 如果接收位置是使用 XmlDefaultPipeline，則訂閱將依賴文件類型。 訂閱是使用內嵌組件資訊，如果組件不存在的話，訂閱將無法執行。 如果您是使用 PassThruPipeline (即為當您公開連接埠，並讓精靈建立接收位置時的預設值)，則訂閱會忽略這項內嵌組件資訊。|  
  
 若要深入了解[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組件與部署，請參閱[BizTalk 組件](../core/biztalk-assemblies.md)。  
  
## <a name="approaches-to-versioning"></a>版本管理的方法  
 規劃專案時，您可以選擇進行下列任一項作業：  
  
-   為某個特定的傳遞標的選擇一個固定的組件編號，且僅遞增檔案版本號碼  
  
-   在開發階段，同時遞增組件版本與檔案版本  
  
 下表為這些方法的比較示意圖。  
  
|固定組件版本，動態檔案版本|動態組件版本，固定或動態檔案版本|  
|--------------------------------------------------|-------------------------------------------------------------|  
|組件版本號碼 = 固定編號<br /><br /> 檔案版本號碼 = 組建編號|組件版本號碼 = 組建編號<br /><br /> 檔案版本號碼 = 組建編號|  
|如果安裝多個組件，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段可能會選取錯誤的組件版本。|就算安裝了多個組件，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 還是會執行最新的組件版本。|  
|任何時候都只能部署一種解決方案版本。|不同版本的解決方案可以一併部署 (雖然解決方案之間的其他部分，例如結構描述定義，有可能會彼此衝突)。|  
|BizTalk 主控件需要重新啟動，才能強制載入更新的組件。|強制 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 載入新的組件。|  
|建立新的部署作業時比較不費力，因為參考組件版本號碼的檔案 (例如繫結檔案與追蹤設定檔) 不需要加以編輯。|部署作業比較費力，因為參考組件版本號碼的檔案需要保持更新為最新版本。|  
  
 如果您要建立一個系統原型，或是開發任何其他類型之工程專用專案，可以選擇使用固定的組件版本與動態檔案版本方法。 如果您不打算將應用程式傳遞給一般使用者，可以將組件版本固定下來，並遞增檔案版本號碼來簡化部署作業並降低相依性被破壞的可能性。 針對版本追蹤，請務必記得為每個組建遞增檔案版本號碼。  
  
 如果您所建立的專案將會傳遞給一般使用者，應該要考慮遞增組件版本，並且選擇性地將有意義的檔案版本號碼儲存起來。 雖然這個方法在修改組建編號以及與其關聯之相依性時會增加額外的工作，卻能夠確保您的組件已更新至最新的版本。 透過使用自動化的部署指令碼，您可以降低版本管理的影響。 若要檢視部署範例，請參閱[應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md)。  
  
> [!NOTE]
>  您所選擇的版本管理機制，應該要能夠確保傳遞正確的檔案，同時簡化維護與功能增強作業。  
  
## <a name="map-function-version-numbering"></a>對應功能版本編號  
 .NET 組件可以叫用從對應中使用**指令碼處理**運算質。 這個方法可以提供很大的彈性，允許開發人員解決許多不同的自訂對應問題。 它也給對應賦予獨特的限制，就是它不只必須從內部參考組件類型名稱，同時也必須從內部參考所叫用的完整組件版本號碼。 如此一來，如果對應所呼叫的組件版本號碼變更了，所有參考該組件的連結也會一併中斷。  
  
 為了避免上述情況發生，如果您需要從對應呼叫組件，我們建議您建立特定的組件來專門保留對應功能，如此便能固定此組件的組件版本號碼。 採用這個方法可讓您在更新其他 helper 函式的組件版本時，維持對應的關係。  
  
 如果對應所參考的組件在對應開發後產生變更，則考慮在「對應編輯器」外更新對應檔來反映更新過的版本號碼。  
  
#### <a name="to-use-notepad-to-modify-the-map-file-to-reflect-updated-version-numbers"></a>使用記事本來修改對應檔以反映更新過的版本號碼  
  
1.  使用**啟動**功能表上，啟動 [記事本]。  
  
2.  在 記事本 在**檔案**功能表上，按一下 **開啟**。 在**開啟**對話方塊中，選取對應檔您想来修改，然後按一下**開啟**。  
  
3.  在 [編輯] 功能表上，按一下 [尋找]。 在**尋找**對話方塊方塊中，輸入**組件 =**，然後按一下 **找下一個**。  
  
4.  如果某個外部組件含有指令碼參考的話，則「記事本」應該會找到如下列所示的 XML 項目：  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c5145e4e089" Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
     更新版本號碼。 如果有多個執行個體，請使用**取代**上**編輯**功能表。  
  
5.  儲存檔案。  
  
     現在您可以使用「對應編輯器」來開啟對應了。  
  
## <a name="see-also"></a>另請參閱  
 [部署 BizTalk 應用程式的最佳作法](../core/best-practices-for-deploying-a-biztalk-application.md)   
 [系統管理員 （BizTalk Server 範例資料夾）](../core/admin-biztalk-server-samples-folder.md)   
 [部署和以程式設計方式啟動協調流程的新版本](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md)
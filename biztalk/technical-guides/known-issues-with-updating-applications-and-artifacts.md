---
title: "已知問題與更新應用程式和成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ea03c-d453-40cc-8ddb-18a96f8ddfe5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a42fb3ca8381faedbd2283b9f4d297738bbb040d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-updating-applications-and-artifacts"></a>更新的應用程式和成品的已知的問題
## <a name="updating-an-application"></a>更新應用程式  
 **移除或刪除成品不會移除它所有的位置**  
  
 移除或刪除成品後，該成品便會從 BizTalk Server 資料庫刪除，因此不會再出現在管理主控台或 BTSTask ListApp 命令所產生的應用程式成品清單中。 它不會移除該成品 Windows 登錄、 全域組件快取 (GAC)、 虛擬目錄或檔案系統中，如果它存在於這些位置。 如果是只存在 BizTalk 管理資料庫的傳送埠、傳送埠群組、接收埠和接收位置，這項作業會將成品完全刪除。  
  
## <a name="updating-an-artifact"></a>更新成品  
 **移除或變更成品的狀態可能會導致不能運作的應用程式**  
  
 當您將參考加入至另一個應用程式，並在其另一個應用程式而定，或移除該成品的成品的狀態進行任何變更時，具有相依性的應用程式將無法正常運作。 如需有關如何變更成品狀態的詳細資訊，請參閱中適當的成品[管理成品](http://go.microsoft.com/fwlink/?LinkID=154725)(http://go.microsoft.com/fwlink/?LinkID=154725)。  
  
 **不支援.NET 原則檔**  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 中不支援 .NET 原則檔的使用。 這是因為原則檔可能無法依預期狀況執行。 原則檔將.NET 重新導向至指定的組件中的版本在 GAC 中，但[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]經常會從快取或 BizTalk 管理資料庫存取組件和成品資料。 根據成品類型、快取狀況以及是否重新啟動主控件執行個體等情況，原則檔可能無法執行所要的作業。  
  
## <a name="updating-an-assembly"></a>更新組件  
 **如果主機並未停止，組件的變更可能不會生效**  
  
 BizTalk 組件必須遵循.NET 版本管理規則。 其主要含意為，一旦針對另一個 .NET 專案或組件 (包括 BizTalk 專案) 的特定版本建置 BizTalk 專案，該專案會繼續使用此版本，直到再針對較新的版本重新建置它為止。  
  
 在開發期間發生的一個與 .NET 版本管理相關之常見問題是，BizTalk 專案上的版本號碼未變更，而且在重新部署組件時，未停止後啟動載入類型的 BizTalk 主控件執行個體。  
  
 當再次執行程序時，變更不會生效。 這是由於將 .NET 組件載入記憶體的方式所造成。 主應用程式已經有組件的記憶體中複本，因為它不會重新載入組件的新複本放在全域組件快取 (GAC) 時。 例如，若已部署和執行搭配協調流程之 1.0.0.0 版的組件，而協調流程已變更，但是版本號碼未變更，則變更不會生效。 在主控件執行個體停止後，會釋放組件的記憶體中複本，當主控件執行個體再次啟動時，它會重新載入組件的新複本並取得變更。 如果已部署新的版本，例如 2.0.0.0 版，將它載入，則變更會生效。  
  
 **變更組件版本可能會破壞組件參考版本的項目之間的關聯性**  
  
 在.NET Framework 開發是一般建置會在執行時，更新組件版本號碼設為目前的組建編號。 然而，在開發 BizTalk 解決方案時，變更組件版本號碼有可能會將組件與透過其組件版本號碼來參考 DLL 的相依項目之間的關係中斷。 下表列出使用其版本號碼和變更的組件版本號碼的效果，請參閱 BizTalk Server 組件的項目。  
  
|實體|變更組件版本號碼所產生的影響|  
|------------|------------------------------------------------|  
|繫結檔案|變更組件版本號碼會導致任何參考組件的現有繫結檔案無法執行。 這是因為繫結檔案會透過包含版本號碼的屬性來參考組件。<br /><br /> 您可以使用「記事本」或其他編輯程式來更新繫結檔案中的版本資訊。 您可以也重新部署方案，並重新產生使用 「 BizTalk Server 管理主控台的 繫結檔案。 最後，您可以使用指令碼，自動化部署與版本管理的作業。 如需有關部署的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkID=154210)(http://go.microsoft.com/fwlink/?LinkID=154210)。|  
|BAM 追蹤設定檔定義 (.btt) 檔案|變更組件版本號碼會導致任何現有的 BAM 追蹤設定檔定義檔案無法執行。 由於 BAM 追蹤檔為二進位檔案格式，您無法加以編輯，只能重新產生新的追蹤檔。 如果需要 BAM 追蹤設定檔，則您可能需要進行下列任一項動作：<br /><br /> 為避免常常更新版本號碼，在建置程序<br />-延遲組建 BAM 追蹤設定檔之前的版本號碼穩定|  
|使用 Web 服務發佈精靈來發佈 Web 服務|當 Web 服務發佈精靈用來產生 ASP.NET Web 介面時，BizTalk Server 組件的組件版本會包含在 ASP.NET 原始程式碼中。 組件版本號碼是在 ASP.NET 介面的執行階段使用，做為 Web 服務作業的 bodyTypeAssemblyQualifiedName 屬性的一部分。 如果 BizTalk Server 組件的版本號碼變更而未更新 bodyTypeAssemblyQualifiedName 屬性，將會由 BizTalk Server 拒絕後續的 Web 服務作業。<br /><br /> 如果接收位置是使用 XmlDefaultPipeline，則訂閱將依賴文件類型。 訂閱是使用內嵌組件資訊，如果組件不存在的話，訂閱將無法執行。 如果您是使用 PassThruPipeline (即為當您公開連接埠，並讓精靈建立接收位置時的預設值)，則訂閱會忽略這項內嵌組件資訊。|
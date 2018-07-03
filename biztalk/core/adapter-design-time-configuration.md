---
title: 配接器設計階段組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5e7b63c-6e17-4c54-9bbf-6964668a2420
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 815690aee7178db52936e8f1aca5641d1be945b6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987367"
---
# <a name="adapter-design-time-configuration"></a>配接器設計階段組態
配接器會同時包含執行階段元件和設計階段元件。 使用者看不到執行階段元件。 該元件是以通透性的方式負責 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息的傳輸、接收和處理。  
  
 配接器的設計階段元件則可透過管理使用者介面顯示。 該元件負責顯示可用屬性、接受管理輸入，並驗證該輸入以設定配接器。 設計階段元件必須可用來正確設定配接器的屬性，以啟用正確交換訊息的執行階段功能，這點非常重要。  
  
 本節僅討論配接器的設計階段元件。 因此，我們的討論只會著重於如何顯示及設定配接器的組態。 有兩種設定配接器的方式：  
  
- **屬性瀏覽器。** 配接器屬性，傳送或接收埠或傳送或接收處理常式，已透過其內容功能表使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。 在這些成品的設定期間會選取配接器 (傳輸)，而且藉由使用屬性瀏覽器來設定其屬性。 可套用的屬性會透過結構描述，以固定的名稱顯示。 例如，如果是傳送 (傳輸) 處理常式，則其屬性會在 TransmitHandler.xsd 檔案中；如果是接收位置，則屬性會在 ReceiveLocation.xsd 檔案中。  此配接器會實作**IAdapterConfig**來尋找並載入適當的結構描述，以公開屬性瀏覽器中的特定屬性的介面。 **IAdapterConfigValidation**介面用來驗證這些項目，並做出任何最後的值之前儲存組態資料。  
  
- **新增配接器中繼資料精靈。** 在應用程式和資料庫配接器，您可能需要支援描述訊息類型和連接埠類型的配接器需要在 BizTalk 專案中的結構描述匯入[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。 或者，有時候也需要使用配接器所提供的服務。 新增配接器中繼資料精靈可用來檢視配接器所支援的服務，並將相關的訊息類型和連接埠類型匯入至專案中。 這種程序稱為「中繼資料收集」(Metadata Harvest)。 身為配接器開發人員建立描述這些服務的 XML 檔案，並在設計階段透過將它公開給精靈**IStaticAdapterConfig**或是**IDynamicAdapterConfig**介面，使用下列結果：  
  
  -   **靜態配接器。** ：此精靈提供標準的預設階層樹狀結構，該結構可用來顯示配接器的服務。 靜態配接器是定義為使用精靈所提供之標準樹狀結構使用者介面 (UI) 的配接器。 使用**IStaticAdapterConfig.GetServiceOrganization**並**GetServiceDescription**方法，以允許所選的服務，可以加入至 BizTalk 專案。 對配接器開發人員來說，這是最簡單的組態選項，但缺點是顯示格式缺乏彈性。  
  
  -   **動態配接器。** ：如果此精靈所提供的基本服務選擇 UI 彈性不足，無法滿足您的 UI 需求，您可以建立自訂 UI，由精靈以動態的方式顯示。 使用**IDynamicAdapterConfig.DisplayUI**方法，以顯示自訂 UI，可以選擇的服務新增至 BizTalk 專案。  
  
  本節提供以靜態或動態方式處理設計階段組態的兩組指導方針。  
  
  Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] software development kit (SDK) 包含您可以使用範例 file 配接器當做範本來建立和自訂自己的配接器設計階段組態解決方案。 在每一個設計階段組態主題中，都有提供關於該範例 FILE 配接器的注意事項及參考，可協助您修改自己的自訂配接器組態需求。 若要進一步瞭解這些指導方針，可能需要安裝、建置及執行 SDK 中提供的範例 FILE 配接器。 請參閱[File 配接器 （BizTalk Server 範例）](../core/file-adapter-biztalk-server-sample.md)如需詳細資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [靜態設計階段配接器設定](../core/static-design-time-adapter-configuration.md)  
  
-   [動態設計階段配接器設定](../core/dynamic-design-time-adapter-configuration.md)  
  
-   [配接器設定結構描述](../core/adapter-configuration-schemas.md)  
  
-   [配接器 WSDL 檔案](../core/adapter-wsdl-files.md)  
  
-   [配接器 GetSchema 方法](../core/adapter-getschema-method.md)  
  
-   [配接器註冊檔案](../core/adapter-registration-file.md)  
  
-   [將配接器安裝到 BizTalk Server 中](../core/install-the-adapter-into-biztalk-server.md)  
  
-   [建置和測試配接器專案](../core/build-and-test-the-adapter-project.md)
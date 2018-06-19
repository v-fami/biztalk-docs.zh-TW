---
title: 擴充路線設計工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f26b825b-ebab-4dac-b7ed-0608c79e146a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78490c7b6447ddb097c0ca61154aab20c44086c3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974476"
---
# <a name="extending-the-itinerary-designer"></a>擴充路線設計工具
路線設計工具是 visual 的特定領域語言 (DSL) for Microsoft Visual Studio 可讓旅搭配使用圖形化模型[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 在設計工具會公開各種擴充點，開發人員可以撰寫自訂延伸模組，以啟用新功能及/或新的組態選項。  
  

  
 **建立自訂的路線匯出工具**  
  
 路線設計工具的架構可以建立自訂模型匯入程式會序列化並將保存路線模型中的資料。  
  
 **為訊息的服務建立自訂的擴充性**  
  
 在路線設計工具的架構可讓您建立可用來將屬性加入至使用的屬性包傳訊服務路線服務模型項目的自訂擴充項。  
  
 如需如何建立這類擴充性的範例，請參閱[安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。  
  
 **建立協調流程為基礎的路線服務的自訂擴充性**  
  
 在路線設計工具的架構可讓您建立自訂的行程服務模型項目可以用來將屬性加入至使用的屬性包，協調流程為基礎的路線服務的擴充項。  
  
 如需如何建立這類擴充性的範例，請參閱[安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。  
  
 **建立自訂解析程式擴充性**  
  
 在路線設計工具的架構可讓您建立自訂的擴充項的自訂解析程式的組態。 這些擴充項提供圖形化介面中解析程式的連接字串中，設定名稱 / 值組的對應到特定的解析程式擴充項類別中的屬性。  
  
 如需如何建立這類擴充性的範例，請參閱[安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。  
  
 **建立自訂配接器屬性的資訊清單檔案**  
  
 在建立自訂配接器提供者，則您也必須提供設計工具支援配接器提供者顯示的端點設定屬性的解析程式擴充項。 若要啟用設計工具支援，就必須建立配接器提供者資訊清單檔案。  
  
 配接器提供者資訊清單檔案會定義特定的配接器提供者、 其類型、 描述和組件中可以找到它們與相關聯的屬性。 這些資訊清單檔案應該置於具有唯一的名稱 (例如，FTPPropertyManifest.xml) 路線設計工具二進位檔 (例如，Microsoft.Practices.Itineary.DslPackage.dll) 相同的資料夾。  
  
 以下是配接器提供者資訊清單檔案的參考執行個體同樣地應該結構化自訂資訊清單檔案。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<adapterPropertyManifest adapterName="FTP">  
     <aliases>  
          <alias name="globalPropertySchemas" value="Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     </aliases>  
     <properties>  
          <property name="UserName" type="FTP.UserName" description="The user name for the connection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="Password" type="FTP.Password" description="The password for the conection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="MaxConnections" type="FTP.MaxConnections" description="The maximun number of connections." assembly="globalPropertySchemas" />  
          <property name="EventArgs" type="System.EventArgs" assembly="mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
     </properties>  
</adapterPropertyManifest>  
```  
  
 **建立自訂篩選器擴充項**  
  
 在路線設計工具的架構可讓您建立的自訂篩選器設定的自訂擴充項。 這些擴充項提供圖形化介面來設定篩選連接字串中的名稱 / 值組對應到特定篩選器 extender 類別中的屬性。  
  
-   / 範例/設計工具擴充性 Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample  
  
-   / 範例/設計工具擴充性 Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample  
  
 **建立自訂驗證規則**  
  
 路線設計工具所導入的最後一個重要延伸模組是一種驗證機制，可讓您可在外部，相對於特定領域語言 (DSL)，指定並實作模型的驗證規則。 機制"連結到"DSL 驗證架構，並在使用者按一下，就會啟用**驗證**或**驗證所有**模型的快顯功能表。 這樣會叫用 DSL 架構**DslCommandSet** ，又呼叫驗證引擎在路線設計工具中的物件。  
  
 **ValidationEngine**類別執行使用企業程式庫驗證應用程式區塊模型項目驗證，並將驗證錯誤記錄到 Microsoft Visual Studio IDE 中的 [錯誤清單] 視窗。 企業程式庫組態檔中定義的驗證，應執行的每種類型的模型中的項目。 檔名為 Ruleset.config 和二進位路線設計工具二進位檔的所在位置的資料夾中。 下列範例是組態檔片段，而且包含兩個驗證規則 （名稱為驗證） **UddiResolver** extender，一個用於**ServerUrl**屬性，另一個用於**ServiceKey**屬性。  
  
```  
<!--   
UddiResolver  
-->  
<type assemblyName="Microsoft.Practices.Services.Extenders.Resolvers.UDDI"  
 name="Microsoft.Practices.Services.Extenders.Resolvers.UDDI.UddiResolver">  
<ruleset name="Menu">  
<properties>  
<property name="ServerUrl">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServerUrl not null validator"/>  
</property>  
<property name="ServiceKey">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServiceKey not null validator"/>  
</property>  
</properties>  
</ruleset>  
</type>  
```  
  
 每個規則會識別驗證器實作的規則。 路線設計工具隨附一組大型驗證程式類別。 它們都放在 Microsoft.Practices.Modeling.Validation 資料夾中的專案設計工具二進位。  
  
 使用此驗證機制的最終結果是使用者可以修改提供的規則和驗證程式變更或新增自己的規則和驗證程式的模型驗證如何該路線設計工具。 這可以完成而不開啟、 修改、 重建和重新部署 Dsl 藉由執行下列兩個步驟：  
  
1.  建立驗證程式類別，並將其放在二進位資料夾內的程式庫位置**Microsoft.Practices.Modeling.Validation.dll**位於程式庫。  
  
2.  將項目加入至 Rules.config 檔案，以定義應該套用的驗證程式哪些模型項目類別的哪些屬性。
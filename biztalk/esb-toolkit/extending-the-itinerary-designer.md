---
title: 延伸路線設計工具 |Microsoft Docs
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
ms.openlocfilehash: 9fbe9e24560f8f00f4b3d806c76ebc326240add5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980743"
---
# <a name="extending-the-itinerary-designer"></a>延伸路線設計工具
在路線設計工具是視覺化的特定領域語言 (DSL) for Microsoft Visual Studio，可讓用於路線的圖形化模型[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。 設計工具會公開各種不同的開發人員可以撰寫自訂的延伸模組，以啟用新功能及/或新的組態選項的擴充點。  
  

  
 **建立自訂路線匯出工具**  
  
 在路線設計工具的架構可讓您建立的自訂模型匯出工具會序列化並將保存路線模型中的資料。  
  
 **建立自訂擴充項的訊息服務**  
  
 在路線設計工具的架構可讓您建立自訂路線服務模型項目可以訊息處理服務用來將屬性加入至使用的屬性包 extender。  
  
 如需如何建立這類擴充性的範例，請參閱 <<c0> [ 安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。  
  
 **建立自訂的擴充性的協調流程為基礎的路線服務**  
  
 在路線設計工具的架構可讓您建立自訂路線服務模型項目可以用來將屬性加入至使用的屬性包，協調流程路線服務的 extender。  
  
 如需如何建立這類擴充性的範例，請參閱 <<c0> [ 安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。  
  
 **建立自訂解析程式擴充項**  
  
 在路線設計工具的架構可讓您建立之設定的自訂解析程式的自訂擴充項。 這些擴充項提供圖形化介面設定的名稱 / 值組在解析程式的連接字串中，對應到特定的解析程式擴充項類別中的屬性。  
  
 如需如何建立這類擴充性的範例，請參閱 <<c0> [ 安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)。  
  
 **建立自訂的配接器屬性的資訊清單檔案**  
  
 在建立自訂配接器提供者時，您必須也提供設計工具支援配接器提供者，這些會顯示端點的組態屬性的解析程式擴充項。 若要啟用設計工具支援，就必須建立配接器提供者資訊清單檔案。  
  
 配接器提供者資訊清單檔會定義與特定配接器提供者、 其類型、 描述，以及在其中可以找到這些組件相關聯的屬性。 這些資訊清單檔應該放在路線設計工具二進位檔 (例如 Microsoft.Practices.Itineary.DslPackage.dll) 的唯一名稱 (例如 FTPPropertyManifest.xml) 相同的資料夾中。  
  
 以下是配接器提供者資訊清單檔案; 的參考執行個體同樣地應該結構化自訂資訊清單檔案。  
  
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
  
 在路線設計工具的架構可讓您建立自訂的擴充項自訂篩選器的組態。 這些擴充項提供圖形化介面設定名稱 / 值組在篩選器連接字串中，對應到特定的篩選器擴充項類別中的屬性。  
  
- / 範例/設計工具擴充性 Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample  
  
- / 範例/設計工具擴充性 Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample  
  
  **建立自訂驗證規則**  
  
  路線設計工具所導入的最後一個重要延伸模組是一種驗證機制，可讓您可在外部，相對於特定領域語言 (DSL)，指定並實作模型驗證規則。 機制 」 連結到 「 DSL 驗證架構，以及當使用者按一下 啟動**Validate**或是**驗證所有**模型的快顯功能表。 這樣會叫用 DSL 架構**DslCommandSet**物件，接著，呼叫在路線設計工具中的 驗證引擎。  
  
  **ValidationEngine**類別會執行使用企業程式庫驗證應用程式區塊的項目模型驗證，並記錄到 Microsoft Visual Studio IDE 中的 錯誤清單 視窗的 驗證錯誤。 Enterprise Library 組態檔中定義的驗證，應該執行的每一種模型中的項目。 檔案命名為 Ruleset.config，且位於 [二進位] 資料夾，所有的路線設計工具二進位檔的所在位置。 下列範例是組態檔片段，並包含兩個驗證規則 （名為驗證程式） **UddiResolver**擴充性、 適合**ServerUrl**屬性，另一個用於**ServiceKey**屬性。  
  
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
  
 每個規則會識別的驗證程式實作的規則。 在路線設計工具隨附大量的驗證程式類別。 它們都放在 Microsoft.Practices.Modeling.Validation 資料夾中的專案設計工具二進位。  
  
 使用此驗證機制的最終結果是使用者可以藉由變更所提供的規則和驗證程式，或藉由新增自己的規則和驗證程式的模型驗證如何修改該路線設計工具。 這可以完成而不需要開啟、 修改、 重建和重新部署的 Dsl，藉由執行下列兩個步驟：  
  
1.  建立驗證程式類別，並將它放在二進位資料夾內的文件庫中何處**Microsoft.Practices.Modeling.Validation.dll**位於程式庫。  
  
2.  將項目加入 Rules.config 檔案來定義應套用的驗證程式的模型項目類別的哪些屬性。
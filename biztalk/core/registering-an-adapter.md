---
title: "註冊配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc85b96e-7b7b-4131-88ec-87b419a61bc2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cc195a55b38a232880ed04108d5a533afd1a311
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="registering-an-adapter"></a>登錄配接器
如果您正在開發自訂配接器，您可以使用 BizTalk Server 註冊修改和執行其中一種隨附於軟體開發套件 (SDK) 中範例 file 配接器的登錄檔案。 或者，您可以使用配接器登錄精靈來建立登錄檔案。 此精靈位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Utilities\AdapterRegistryWizard 資料夾中。  
  
> [!IMPORTANT]
>  -   32 位元電腦上，必須從命令提示字元執行配接器登錄精靈所產生的登錄 (.reg) 檔案。  
> -   64 位元電腦上，配接器登錄精靈所產生的登錄 (.reg) 檔案必須執行從 32 位元和 64 位元命令提示字元。  
  
 建立登錄項目之後，您可以在 BizTalk Server 管理主控台中新增配接器，或是使用 Windows Management Instrumentation (WMI) 方法，以程式設計的方式完成新增動作。 本主題討論每一個登錄項目，並說明自訂配接器之現有登錄檔的修改位置和修改方式。  
  
 如需使用配接器登錄精靈的指示，請參閱[配接器登錄精靈](../core/adapter-registry-wizard.md)。 如需修改 SDK 隨附之範例登錄檔的指示，請參閱[配接器登錄檔案](../core/adapter-registration-file.md)。  
  
## <a name="registry-keys"></a>登錄機碼  
 您必須建立下列登錄項目才能部署配接器：  
  
 **登錄機碼位置**  
  
```  
[HKEY_CLASSES_ROOT\CLSID\{%uuid of custom transport%}\BizTalk]  
@="BizTalk"  
  
```  
  
 **型別名稱**  
  
 配接器類型名稱可識別 BizTalk Server 電腦中配接器的類型。 任何配接器都必須有這個機碼。  
  
```  
"TransportType"="MyTransportAdapter"  
  
```  
  
 **條件約束**  
  
 配接器條件約束會定義配接器的功能。  
  
 每個配接器都必須有這個機碼。 根據建立的配接器類型而定，您可以修改條件約束的位元遮罩。  
  
```  
"Constraints"=dword:00003C0b  
```  
  
 描述配接卡功能的值可以是下表所示值的組合。  
  
|值|十六進位值|旗標|Description|  
|-----------|---------------|----------|-----------------|  
|1|0x0001|eProtocolSupportsReceive|配接器可支援接收作業。|  
|2|0x0002|eProtocolSupportsTransmit|配接器可支援傳送作業。|  
|8|0x0008|eProtocolReceiveIsCreatable|配接器的接收處理常式採用內含式的主控架構。|  
|128|0x0080|eProtocolSupportsRequestResponse|配接器可支援要求-回應作業。|  
|256|0x0100|eProtocolSupportsSolicitResponse|配接器可支援請求-回應作業。|  
|1024|0x4000|eOutboundProtocolRequiresContextInitialization|指出配接器使用傳送處理常式組態的配接器架構使用者介面。|  
|2048|0x0800|eInboundProtocolRequiresContextInitialization|指出配接器使用接收處理常式組態的配接器架構使用者介面。|  
|4096|0x1000|eReceiveLocationRequiresContextInitialization|指出配接器使用接收位置組態的配接器架構使用者介面。|  
|8192|0x2000|eTransmitLocationRequiresContextInitialization|指出配接器使用傳送埠組態的配接器架構使用者介面。|  
|16384|0x4000|eSupportsOrderedDelivery|指出配接器可支援排序的訊息傳遞。|  
|32768|0x8000|eInitTransmitterOnServiceStart|傳送配接器啟動的時間為服務啟動時，而非傳送第一則訊息時。|  
|65536|0x10000|eSupport32BitOnly|指出配接器只支援在 32 位元主控件中執行。|  
  
### <a name="namespace"></a>命名空間  
 每個配接器都必須為其屬性定義命名空間。 BizTalk Server 會將配接器專用的屬性儲存在此命名空間下的訊息內容中。 所有的配接器都必須有這個屬性。  
  
```  
"PropertyNameSpace"="namespace"  
```  
  
### <a name="aliases"></a>Aliases  
 每個配接器都可能會有一組前置詞，用來唯一識別 BizTalk Server 內的配接器類型。 這可以讓系統在透過動態傳送埠傳送訊息時，解析正確的傳輸類型。 配接器必須在登錄時指定前置詞清單。  
  
```  
"AliasesXML"="<AdapterAliasList><AdapterAlias>sample://</AdapterAlias></AdapterAliasList>"  
```  
  
### <a name="configuration-property-pages"></a>組態屬性頁  
 配接器必須有組態屬性頁，才能設定其接收位置和傳送埠。 每個配接器都會透過指定個別類別 ID 的方式來登錄其屬性頁。  
  
```  
"InboundProtocol_PageProv"="{%CLSID for inbound protocol prop page%}"  
"OutboundProtocol_PageProv"="{%CLSID for outbound protocol prop page%}"  
"ReceiveLocation_PageProv"="{%CLSID for receive location prop page%}"  
"TransmitLocation_PageProv"="{%CLSID for transmit location prop page%}"  
```  
  
 如果配接器使用用來產生屬性頁的配接器架構使用者介面，則必須指定下列登錄機碼值：  
  
```  
"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"  
"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"  
"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"  
"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"  
```  
  
 請注意，如果其中一個端點不是必要項目 (即配接卡只用來傳送或接收)，您可以從登錄中刪除未使用的登錄機碼。  
  
### <a name="runtime-component-registration"></a>執行階段元件登錄  
 配接卡可透過指定執行階段元件的類別 ID (適用於 COM 和 .NET)、類型名稱，以及接收和傳送執行階段的組件路徑，以登錄其執行階段元件。  
  
> [!NOTE]
>  所有**OutboundEngineCLSID**和**InboundEngineCLSID**必須是唯一的索引鍵。 在資料庫中，單一資料列**OutboundEngineCLSID**和**InboundEngineCLSID**可能不同。  
  
```  
"OutboundEngineCLSID"="{%CLSID of outbound transport%}"  
"InboundEngineCLSID"="{%CLSID of inbound transport%}"  
"InboundTypeName"="BizTalk.Samples.Adapters.MyReceiver"  
"OutboundTypeName"="BizTalk.Samples.Adapters.MyTransmitter"  
"InboundAssemblyPath"="C:\Program Files\MyTransport.dll"  
"OutboundAssemblyPath"="C:\Program Files\MyTransport.dll"  
```  
  
> [!NOTE]
>  您可以將配接器的組件安裝到全域組件快取中，然後在登錄檔中參照該組件。  
  
### <a name="registration-of-adapter-properties-for-sso-configuration-store"></a>SSO 組態存放區的配接器屬性登錄  
 配接器必須向 BizTalk Server SSO 資料庫登錄其屬性，才能在設計階段和執行階段中儲存及擷取屬性。  
  
```  
ReceiveHandlerPropertiesXML  
ReceiveLocationPropertiesXML  
SendHandlerPropertiesXML  
SendLocationPropertiesXML  
```  
  
 這些值包含的定義 (結構描述) 是配接器相關之對應實體所容許屬性的定義，可以儲存在組態存放區中。 這些定義以 XML 字串保存，該字串係由內含屬性類型但不含值的屬性包進行還原序列化。 屬性項目若非空白值，表示該屬性已遮罩 (已遮罩代表它是唯讀屬性，而且在系統管理模式下呼叫時，安全存放區 API 並不會傳回該屬性；對於這種屬性，安全存放區 API 會傳回 VT_NULL)。  
  
### <a name="example"></a>範例  
 HTTP 配接器會藉由定義登錄其屬性的 HTTP 傳送埠**SendLocationPropertiesXML**登錄機碼包含下列值：  
  
```  
<CustomProps><Username vt="8"/><Password vt="8">Encrypted</Password><Certificate vt="8"/><RequestTimeout vt="3"/><MaxRedirects vt="3"/><ContentType vt="8"/><UseProxy vt="11"/><ProxyName vt="8"/><ProxyPort vt="3"/><ProxyUsername vt="8"/><ProxyPassword vt="8">Encrypted</ProxyPassword><UseHandlerSetting vt="11"/><AuthenticationScheme vt="8"/><UseSSO vt="11"/><AffiliateApplicationName vt="8"/></CustomProps>  
```  
  
### <a name="registration-of-the-component-as-a-transport-provider"></a>將元件登錄為傳輸提供者  
 配接器必須在登錄中的「實作的類別」屬性下，登錄成傳輸提供者。 此屬性會將其特性識別配接器的取用者。  
  
```  
[HKEY_CLASSES_ROOT\CLSID\{%uuid of custom transport%}\Implemented Categories]  
[HKEY_CLASSES_ROOT\CLSID\{%uuid of custom transport%}\Implemented Categories\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}]  
```  
  
## <a name="see-also"></a>另請參閱  
 [配接器設計問題](../core/adapter-design-issues.md)
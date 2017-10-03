---
title: "建立自訂配接器提供者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb93acf8-fd9d-4315-8690-f0c152a954b5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feb9efa5ad879e86f32ca1963313dadc7e6a9d7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-adapter-provider"></a>建立自訂配接器提供者
解析程式執行與上一節所述之後，動態解析服務會檢查結果是否端點 （不轉換）。 如果端點，服務會具現化配接器管理員，也就是執行個體的**AdapterMgr**類別。  
  
 配接器管理員驗證並修復的傳輸類型及輸出傳輸位置。 如果傳輸類型是仍未解決，而且 URL 開頭為"http"或"https"，配接器管理員將傳輸類型設定為 「 Wcf-wshttp"。  
  
 接下來，配接器管理員確認等同於有效的 Microsoft BizTalk Server 配接器的傳輸類型，然後它會傳回其屬性的命名空間。 此程序只執行一次的所有介面卡，並將結果儲存在快取以避免重複的查詢其他使用相同的配接器的內送訊息。  
  
 配接器管理員使用的傳輸類型 (不含"**://**"後置詞) 來判斷適當的配接器提供者。 配接器提供者是自訂的組件必須實作**IAdapterProvider**介面。 配接器提供者使用的內容**解析**結構**字典**来設定可讓訊息的所有通訊協定特定屬性的解析程式所產生的執行個體Microsoft BizTalk Server 執行階段引擎來執行動態解析。  
  
 像與解析程式 （如上一節中說明），動態解析機制使用的項目 Esb.config 組態檔中尋找配接器提供者。 下列 XML 顯示組態檔的區段。  
  
```xml  
<adapterProviders cacheManager= "Adapter Providers Cache Manager"  absoluteExpiration="3600">  
     <adapterProvider name="WCF-WSHttp" type="Microsoft.Practices.ESB.Adapter.WcfWSHttp.AdapterProvider, Microsoft.Practices.ESB.Adapter.WcfWSHttp, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="Http,Https" />  
     <adapterProvider name="WCF-BasicHttp" type="Microsoft.Practices.ESB.Adapter.WcfBasicHttp.AdapterProvider, Microsoft.Practices.ESB.Adapter.WcfBasicHttp, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="Http,Https" />  
     <adapterProvider name="WCF-Custom" type="Microsoft.Practices.ESB.Adapter.WcfCustom.AdapterProvider, Microsoft.Practices.ESB.Adapter.WcfCustom, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="mssql" />  
     <adapterProvider name="SMTP" type="Microsoft.Practices.ESB.Adapter.SMTP.AdapterProvider, Microsoft.Practices.ESB.Adapter.SMTP, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="smtp" />  
     <adapterProvider name="FTP" type="Microsoft.Practices.ESB.Adapter.FTP.AdapterProvider, Microsoft.Practices.ESB.Adapter.FTP, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
          <adapterConfig>  
               <add name="DefaultUsername" value="anonymous" />  
               <add name="DefaultPassword" value="" />  
          </adapterConfig>  
     </adapterProvider>  
     <adapterProvider name="MQSeries" type="Microsoft.Practices.ESB.Adapter.MQSeries.AdapterProvider, Microsoft.Practices.ESB.Adapter.MQSeries, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="MQS" adapterAssembly="MQSeries, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     <adapterProvider name="FILE" type="Microsoft.Practices.ESB.Adapter.FILE.AdapterProvider, Microsoft.Practices.ESB.Adapter.FILE, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22" moniker="File" />  
</adapterProviders>  
```  
  
## <a name="creating-a-custom-adapter-provider"></a>建立自訂配接器提供者  
 配接器管理員 (執行個體**AdapterMgr**類別) 的組態檔中的配接器提供者尋找並載入適當的組件。 動態解析機制會快取載入的所有具象實作**IAdapterProvider**介面，以避免重複的讀取組態資訊和時數個內送訊息使用載入的組件相同的配接器提供者。  
  
 最後，配接器管理員執行**SetEndPoint**之具象實作的方法**IAdapterProvider**介面和管線元件將訊息傳回至 BizTalkMessagebox 資料庫。  
  
 **若要建立自訂配接器提供者**  
  
1.  建立衍生自的組件**BaseAdapterProvider**基底類別，並包含**SetEndPoint**設定端點的訊息內容屬性的方法。  
  
2.  註冊配接器提供者將它加入至 Esb.config 組態檔使用 **\<adapterProvider >**項目以做為配接器名稱**名稱**屬性，完整做為類別的限定的名稱**類型**屬性，做為 moniker **moniker** （應該以逗號分隔多個值） 的屬性，並選擇性地，實際的配接器的組件做為**adapterAssembly**屬性。  
  
3.  在全域組件快取中註冊新的組件。
---
title: 追蹤 WCF LOB Adapter SDK 的配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a4f4758-3e3e-48c4-b4cf-414c2b05d539
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ca4b68f23f791de3ecd68bc69b85c2908b6d7a0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965356"
---
# <a name="trace-an-adapter-with-the-wcf-lob-adapter-sdk"></a>追蹤 WCF LOB Adapter SDK 的配接器
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]追蹤是建立在 Systems.Diagnostics 之上。 使用追蹤來源 Microsoft.ServiceModel.Channels[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。  使用追蹤來源 Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。 WCF 追蹤會寫入名為 System.ServiceModel 的來源。  
  
 配接器開發人員可以提供使用 Microsoft.ServiceModel.Channels.Common.AdapterTrace 類別之配接器的追蹤來源名稱。 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會產生可用於配接器開發人員所提供的配接器程式碼中的檢測追蹤包裝函式類別。  
  
 如需 WCF 追蹤資訊，請參閱[追蹤](https://msdn.microsoft.com/library/ms730342.aspx)。
  
 如需分析 WCF 中的追蹤資訊，請參閱[服務追蹤檢視器工具 (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx)。 
  
## <a name="sample-trace-wrapper-utility-class"></a>範例追蹤包裝函式的公用程式類別  
  
```  
public class EchoAdapterUtilities  
{  
    static AdapterTrace trace = new AdapterTrace("Microsoft.Adapters.Samples.Echo.EchoAdapter");  
  
    /// <summary>  
    /// Gets the AdapterTrace  
    /// </summary>  
    public static AdapterTrace Trace  
    {  
        get  
        {  
            return trace;  
        }  
    }  
}  
```  
  
 然後由配接器開發人員在配接器程式碼提供檢測資料配接器取用者使用先前的公用程式類別。  
  
 EchoAdapterUtilities.Trace.Trace (System.Diagnostics.TraceEventType.Information，"EchoAdapterConnection::Open 」、 「 已成功開啟連接 ！ 」);  
  
## <a name="enable-tracing-for-the-adapter-and-wcf-lob-adapter-sdk-runtime"></a>啟用配接器和 WCF LOB 配接器 SDK 執行階段的追蹤  
 您可以啟用追蹤中所提供[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]藉由使用配接器的應用程式的 app.config 檔案中新增下一節。  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="Microsoft.Adapters.Samples.Echo.EchoAdapter" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
    <source name="Microsoft.ServiceModel.Channels" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\TestEchoAdapter_Browse.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 您可以使用 新增項目，指定您想要使用的追蹤接聽項的類型與名稱。 在範例組態中，我們將名為接聽程式 」 xmlTrace 」，我們想要使用的類型加入標準的.NET Framework 追蹤接聽項 (System.Diagnostics.XmlWriterTraceListener)。 您可以加入任意數目的每個來源的追蹤接聽項。 例如，在下列範例中，我們也加入另一個名為"textTrace 」 使用.NET Framework 追蹤接聽項 System.Diagnostics.TextWriterTraceListener 的接聽程式。 如果追蹤接聽項將追蹤發出到檔案，您必須在組態檔中指定的輸出檔案位置和名稱。 這是設為 initializeData 檔案的名稱，該接聽項。  
  
## <a name="enabling-tracing-for-the-add-adapter-service-reference-plug-in"></a>啟用追蹤新增配接器服務參考外掛程式  
 您可以啟用追蹤，在此外掛程式的 devenv.exe.config 檔案中加入下一節位於`\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`。
  
```  
<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
</system.diagnostics>  
```  
  
## <a name="enable-tracing-for-the-consume-adapter-service-add-in"></a>啟用追蹤功能使用配接器服務增益集  
 您可以啟用追蹤這個增益集在 BTSNTSVC.exe.config 檔案中加入下列區段`\Program Files (x86)\Microsoft BizTalk Server`。  
  
```  
<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 WCF LOB 配接器 SDK 所建立的配接器進行疑難排解](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)
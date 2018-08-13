---
title: 安裝和執行動態解析範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4359987-b18c-44f5-a2cf-e30e17ac5e9f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0939111bc0a62ecf31286045f412ed160a97c3f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967727"
---
# <a name="installing-and-running-the-dynamic-resolution-sample"></a>安裝和執行動態解析範例
動態解析範例示範的 ESB 發送器和 ESB 發送器解譯器管線元件的一般使用案例。 它示範如何使用元件動態解析端點位置、 設定路由的屬性，並解決並執行 Microsoft BizTalk 對應，在訊息層級，而不需使用協調流程。 它也會示範單向和雙向傳訊模式。  
  
> [!NOTE]
>  為了取得最佳結果，當解析機制，在您熟悉[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，您應該執行[安裝和執行解析程式服務範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)執行動態解析範例之前。  
  
 範例應用程式包含兩個接收位置和兩個動態傳送埠，此範例會示範多個使用動態解析元件的使用案例。 每個使用案例會示範如何解析程式和配接器提供者，在解決和配接器提供者架構，用來結合，可以提供各式各樣的鬆散偶合的傳訊解決方案的基礎。  
  
## <a name="one-way-messaging-scenarios"></a>單向傳訊案例  
 全都是單向傳訊案例 （除了使用 XPATH 解析程式） 使用檔案 NAOrderDoc.xml，位於 [\Source\Samples\DynamicResolution\Test\Data] 資料夾中，輸入接收位置名為 DynamicResolution_FILE。 有七個單向的訊息範例中，所有由唯一的繫結檔案，您必須匯入，然後再執行每個範例。  
  
## <a name="two-way-messaging-scenarios"></a>雙向傳訊案例  
 所有的雙向傳訊案例使用範例 ESB。NorthAmericanServices Web 服務位於 http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx 發佈到 BizTalk 的要求訊息。 您可以執行使用 Microsoft InfoPath 此 Web 服務或透過公用程式，例如可從 Storm [CodePlex](http://go.microsoft.com/fwlink/?LinkID=187762&clcid=0x409)。  
  
 每個範例，動態地解析提交訊息至範例 ESB 的端點 URL。CanadianServices Web 服務位於http://localhost/ESB.CanadianServices/SubmitPOService.asmx。 此範例會執行**submitOrder**動作或**submitPurchase**動作，根據解析程序的結果。 雙向傳訊案例的接收位置是 DynamicResolutionReqResp_SOAP。 有 10 個的雙向傳訊範例中，所有由唯一的繫結檔案，您必須匯入，然後再執行每個範例。  
  
## <a name="binding-files"></a>繫結檔案  
 此範例的繫結檔案位於名為 \Source\Samples\DynamicResolution\Samples\Release 資料夾中。  
  
 所有的繫結檔案名稱的開頭 GlobalBank.ESB.DynamicResolution_SubmitOrder_To，後面接著所套用之個別範例的指示。 比方說，繫結檔案，例如 「 檔案輸出到檔案輸入會使用靜態的解析程式 」 是 GlobalBank.ESB.DynamicResolution_SubmitOrder_To_FILE_To_FILE_STATIC_Bindings.xml。  
  
 每次您匯入其中一個繫結至 GlobalBank.ESB BizTalk 應用程式，基礎的檔案接收位置內的範例應用程式會重設。 在 接收埠名稱相關聯的動態傳送埠篩選條件。 因此，若要執行測試，只匯入其中一個繫結檔案，請卸除的適當命名的訊息則輸入資料夾 （適用於單向傳訊的案例），或呼叫使用 InfoPath、 Storm 公用程式，或任何其他的 NorthAmerican Web 服務適合的用戶端。  
  
## <a name="sample-dependencies"></a>範例相依性  
 動態解析範例有多個核心 ESB 安裝一部分的組件的相依性。 這些組件如下所示：  
  
- **Microsoft.Practices.ESB.PipelineComponents.dll**。 這包含 ESB 發送器管線元件。  
  
- **Microsoft.Practices.ESB.Resolver.dll**。 這會實作管線由呼叫的解析程式管理員。  
  
- **Microsoft.Practices.ESB.Resolver.BRE.dll**。 這會實作商務規則引擎的解析程式。  
  
- **Microsoft.Practices.ESB.Resolver.STATIC.dll**。 這會實作靜態的解析程式。  
  
- **Microsoft.Practices.ESB.Resolver.UDDI.dll**。 這會實作 UDDI 解析程式。  
  
- **Microsoft.Practices.ESB.Resolver.UDDI3.dll**。 這會實作 UDDI3 解析程式。  
  
- **Microsoft.Practices.ESB.Resolver.XPATH.dll**。 這會實作 XPATH 解析程式。  
  
- **Microsoft.Practices.ESB.Resolver.Schemas.dll**。 這包含解析程式的結構描述。  
  
- **Microsoft.Practices.ESB.Adapter.dll**。 這會實作配接器管理員。  
  
- **Microsoft.Practices.ESB.Adapter.FTP.dll**。 這會實作 FTP 配接器提供者。  
  
- **Microsoft.Practices.ESB.Adapter.FILE.dll**。 這會實作檔案配接器提供者。  
  
- **Microsoft.Practices.ESB.Adapter.MQSeries.dll**。 這會實作 MQSeries 配接器提供者。  
  
- **Microsoft.Practices.ESB.Adapter.WcfBasicHttp.dll**。 這會實作 Wcf-basichttp 配接器提供者。  
  
- **Microsoft.Practices.ESB.Adapter.WcfWSHttp.dll**。 這會實作 Wcf-wshttp 配接器提供者。  
  
  動態解析範例也是取決於先前的解析程式和配接器的正確組態。 請確定您在安裝中所述完成處理程序設定這些項目， [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。  
  
  本節包含下列主題：  
  
- [安裝動態解析範例](../esb-toolkit/installing-the-dynamic-resolution-sample.md)  
  
- [執行動態解析範例](../esb-toolkit/running-the-dynamic-resolution-sample.md)

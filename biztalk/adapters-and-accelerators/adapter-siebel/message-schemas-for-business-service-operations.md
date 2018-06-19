---
title: 商務服務作業的訊息結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message schemas, for business service methods
ms.assetid: ba23248b-5d73-4de0-9f7c-987cd88a4b63
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0062b8e6b6ce3961c937e9e5bece81cb24281049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222294"
---
# <a name="message-schemas-for-business-service-operations"></a>商務服務作業的訊息結構描述
Siebel 商務服務是可以在 Siebel 系統直接叫用的商務方法的集合。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]呈現的 Siebel 商務服務的商務方法做為作業。  
  
## <a name="message-schemas-for-siebel-business-service-method-operations"></a>Siebel 商務服務方法作業的訊息結構描述  
 下表顯示的訊息結構描述所呈現的 Siebel 商務服務方法操作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
|作業|XML 結構|Description|  
|---------------|-------------------|-----------------|  
|[Business_Service_METHOD_NAME]|商務服務方法要求訊息：<br /><br /> `<[METHOD_NAME] xmlns="[VERSION]/BusinessServices/[Business Service]/Operation">   <[METHOD_NAME]RequestRecord>     <[I_PRM1_NAME]>value1</[I_PRM1_NAME]>     <[I_PRM2_NAME]>value2</[I_PRM2_NAME]>     …   </[METHOD_NAME]RequestRecord>   <[METHOD_NAME]InOutRecord>     <[IO_PRM1_NAME]>value1</[IO_PRM1_NAME]>     <[IO_PRM2_NAME]>value2</[IO_PRM2_NAME]>     …   </[METHOD_NAME]InOutRecord> </[METHOD_NAME]>`<br /><br /> [版本] = 訊息版本字串。例如，"http://Microsoft.LobServices.Siebel/2007/03。 」<br /><br /> [商務服務] = 商務服務; 的名稱例如，ExtractDataService。<br /><br /> [METHOD_NAME] = 商務服務方法的名稱例如，ExecuteNext。<br /><br /> [I_PRM_NAME] = 名稱的 IN 參數。<br /><br /> [IO_PRM_NAME] = 名稱的 IN OUT 參數。<br /><br /> 商務服務方法的回應訊息：<br /><br /> `<[METHOD_NAME]Response xmlns="[VERSION]/BusinessServices/[Business Service]/Operation">   <[METHOD_NAME]Result>     <[O_PRM1_NAME]>value1</[O_PRM1_NAME]>     <[O_PRM2_NAME]>value2</[O_PRM2_NAME]>     …   </[METHOD_NAME]Result>   <[METHOD_NAME]InOutRecord>     <[IO_PRM1_NAME]>value1</[IO_PRM1_NAME]>     <[IO_PRM2_NAME]>value2</[IO_PRM2_NAME]>     …   </[METHOD_NAME]InOutRecord > </[METHOD_NAME]Response>`<br /><br /> [版本] = 訊息版本字串。例如，"http://Microsoft.LobServices.Siebel/2007/03。 」<br /><br /> [商務服務] = 商務服務; 的名稱例如，ExtractDataService。<br /><br /> [METHOD_NAME] = 商務服務方法的名稱例如，ExecuteNext。<br /><br /> [O_PRM_NAME] = 名稱的 OUT 參數。<br /><br /> [IO_PRM_NAME] = INOUT 名稱參數。<br /><br /> **重要事項：** 出 IN 和 OUT 參數會一律標示為選擇性，在中繼資料，即使它們 Siebel 系統所需。 因此，如果參數標示為選擇性但 Siebel 系統所需的中繼資料中，配接器會擲回`TargetSystemException`接收自 Siebel 而非`XmlReaderParsingException`。|Siebel 商務服務方法會呈現為作業名稱。<br /><br /> -在中，在 OUT 輸出參數支援。<br /><br /> 顯示階層式的類型為字串。 Siebel 配接器不會驗證這些字串傳遞的值。 如果這些值不符合預期的 Siebel 系統的結構描述，就會產生執行階段例外狀況。|  
  
## <a name="message-actions-for-siebel-business-service-method-operations"></a>Siebel 商務服務方法作業的訊息動作  
 下表顯示如何形成 Siebel 商務服務方法的 SOAP 動作。 僅要求訊息的動作會顯示，動作的回應訊息會形成是將 k-1"/ 回應 」 至要求訊息的動作;例如，"[VERSION] / BusinessServices/ExtractDataService/ExecuteNext/回應 」。  
  
|作業|動作|Description|  
|---------------|------------|-----------------|  
|[Business_Service_METHOD_NAME]|[版本] /BusinessServices/ [商務服務] / [Business_Service_METHOD_NAME]|[版本] / BusinessServices/ExtractDataService/ExecuteNext|  
  
 [版本] = 訊息版本字串。例如，"http://Microsoft.LobServices.Siebel/2007/03。 」  
  
 [商務服務] = 商務服務; 的名稱例如，ExtractDataService。  
  
 [Business_Service_METHOD_NAME] = 商務服務方法的名稱例如，ExecuteNext。  
  
 當您使用時，您必須明確指定的訊息動作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]在 BizTalk Server 解決方案，或使用 WCF 通道模型。 如需詳細資訊，請參閱[開發 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)。  
  
## <a name="siebel-business-service-wcf-client-methods"></a>Siebel 商務服務的 WCF 用戶端方法  
 下表顯示[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方法簽章所產生的[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]siebel 商務服務方法。  
  
|作業|WCF 服務模型方法|  
|---------------|------------------------------|  
|[Business_Service_METHOD_NAME]|`[Business_Service_METHOD_NAME]ResponseRecord client.[Business_Service_METHOD_NAME]([Business_Service_METHOD_NAME]RequestRecord);`<br /><br /> [Business_Service_METHOD_NAME] = 商務服務方法的名稱。例如，ExecuteNext。|  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Siebel eBusiness 應用程式](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)
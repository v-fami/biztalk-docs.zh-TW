---
title: Microsoft.BizTalk.GlobalPropertySchemas 參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2acf3083-a0a9-483f-88bf-8023d9933e1e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8e24cee64b5f03b212fabd7003f8ba3586b1c22
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982879"
---
# <a name="microsoftbiztalkglobalpropertyschemas-reference"></a>Microsoft.BizTalk.GlobalPropertySchemas 參考
**Microsoft.BizTalk.GlobalPropertySchemas**命名空間包含各種 BizTalk Server 元件所使用之屬性的屬性結構描述。 這個命名空間包含 BizTalk 引擎使用的系統屬性、每個傳輸用來處理組態的傳輸特定屬性，以及設定管線元件的屬性。  

## <a name="namespace-schemas"></a>命名空間的結構描述  

 下表顯示中包含的全域屬性結構描述**Microsoft.BizTalk.GlobalPropertySchemas**命名空間。  


|                                                                                                                                                              屬性結構描述                                                                                                                                                              |                                                                                                                                                               功能範圍和描述                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                          bts-btf2-properties.xsd                                                                                                                                                          |                                                                                                                                                                     屬性結構描述。                                                                                                                                                                      |
|                                             btf2-endpoints-header.xsd<br /><br /> btf2-envelope.xsd<br /><br /> btf2-manifest-header.xsd<br /><br /> btf2-process-header.xsd<br /><br /> btf2-properties-header.xsd<br /><br /> btf2-receipt-header.xsd<br /><br /> btf2-services-header.xsd                                              |                                                                                                   定義 BizTalk Framework 建構的結構描述。 這些結構描述是 BizTalk Framework 組合器和解譯器管線元件的特定結構描述。                                                                                                   |
|                                                                                                                                                         bts-system-properties.xsd                                                                                                                                                         | 這是系統屬性結構描述。 BizTalk 引擎使用這個結構描述中的大部分屬性。 您可以使用其中一些屬性來進行訊息路由。 如需有關可用於訊息路由的屬性的詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 |
|                                                                                                                                                        bts-endpoint-properties.xsd                                                                                                                                                        |                                                                                                                                                           這是內部屬性結構描述。                                                                                                                                                            |
|                                                                                                                                      bts-mime-properties.xsd<br /><br /> bts-xmlnorm-properties.xsd                                                                                                                                       |                                                                                                      這些是用於下列管線元件的屬性結構描述：MIME、XML、一般檔案和 BizTalk Framework 組合器和解譯器等管線元件。                                                                                                      |
|                                                                                                                                                    bts-messagetracking-properties.xsd                                                                                                                                                     |                                                                                                                                                           追蹤引擎使用這個結構描述。                                                                                                                                                           |
| bts-file-properties.xsd<br /><br /> bts-ftp-properties.xsd<br /><br /> bts-http-properties.xsd<br /><br /> bts-pop3-properties.xsd<br /><br /> bts-smtp-properties.xsd<br /><br /> soap-encoding_1__1.xsd<br /><br /> soap-envelope_1__1.xsd<br /><br /> bts-soap-properties.xsd<br /><br /> bts-WindowsSharePointServices-properties.xsd |                                                               這些是傳輸專用的屬性結構描述。 傳輸使用這些結構描述來傳送特定的傳輸資訊和組態。 如需有關傳輸的詳細資訊，請參閱[使用配接器](../core/using-adapters.md)。                                                                |
|                                                                                                                                                        XLANGsBizTalkProperties.xsd                                                                                                                                                        |                                                                                                                                                        協調流程引擎使用這個結構描述。                                                                                                                                                         |

## <a name="see-also"></a>另請參閱  
 [關於在 BizTalk 專案中包含的 BizTalk 命名空間參考](../core/about-biztalk-namespace-references-included-in-biztalk-projects.md)
---
title: EDI 服務和控制結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4866571b-b12d-446c-8d27-a72fe7e479ef
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 480a86ccb001ec31a12ca82588a4db61721e1145
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968319"
---
# <a name="edi-service-and-control-schemas"></a>EDI 服務和控制結構描述
控制結構描述是處理訊息信封 (標頭控制結構描述) 和通知的要件。 安裝程式將這些結構描述部署在 Microsoft.BizTalk.Edi.BaseArtifacts.dll 中。 這些結構描述不一定要加入至 BizTalk 專案，因為它們是部署在 BaseArtifacts.dll 中。 您必須將 BaseArtifacts.dll 組件的參考加入至包含結構描述的專案，才能使用這些結構描述。  

## <a name="envelope-service-schemas"></a>信封服務結構描述  
 服務結構描述 X12ServiceSchema 和 EdifactServiceSchema 可用來驗證交換、群組，以及 EDI 交換信封中的交易集標頭和結尾。 這適用於所有的 EDI 交換： 批次的交換、 批次的交換分割或保留的批次的交換。 這些結構描述的命名空間 http://schemas.microsoft.com/Edi/X12ServiceSchema 和 http://schemas.microsoft.com/Edi/EdifactServiceSchema 。  

 若 EDI 交換是保留的批次交換，則除了服務結構描述，BizTalk 執行階段還會使用批次結構描述 X12_BatchSchema 和 Edifact_BatchSchema。 如需詳細資訊，請參閱 < [EDI 批次結構描述](../core/edi-batch-schemas.md)。  

 您可以在這些結構描述中自訂識別碼欄位列舉， 但不允許進行其他修改。 如需詳細資訊，請參閱 <<c0> [ 信封結構描述中的自訂列舉](../core/customizing-enumerations-in-the-envelope-schema.md)。  

## <a name="acknowledgment-control-schemas"></a>通知控制結構描述  
 EDI 接收管線會使用通知結構描述來產生要傳送的通知，而 EDI 傳送管線會使用通知結構描述來處理收到的通知。 這些結構描述包括適用於 X12 編碼的 997 功能通知結構描述和 TA1 交換通知結構描述，以及適用於 EDIFACT 編碼的 CONTRL 結構描述，如下表所示。 您無法修改這些結構描述。  


|      通知       |     結構描述名稱      |             目標命名空間             |                               Root                                |
|----------------|----------------------|------------------------------------------|-------------------------------------------------------------------|
|    X12 TA1     |    X12_TA1Schema     |   http://schemas.microsoft.com/Edi/X12   |                   TA1<br /><br /> X12_TA1_Root                    |
|    X12 997     |    X12_997Schema     |   http://schemas.microsoft.com/Edi/X12   |            ST<br /><br /> SE<br /><br /> X12_997_Root             |
| EDIFACT CONTRL | Edifact_ContrlSchema | http://schemas.microsoft.com/Edi/Edifact | Efact_Contrl_Root<br /><br /> UCD<br /><br /> UCM<br /><br /> UCS |

 針對 X12 編碼，997 功能通知結構描述會定義交換、群組、訊息信封中使用的交易集/訊息標頭和結尾，以及報告內文驗證結果的 AK1、AK2、AK3、AK4、AK5 和 AK9 區段。 TA1 技術通知結構描述則會定義交換標頭和結尾，以及報告標頭驗證結果的 TA1 通知區段。 這些結構描述的命名慣例是 x12_<\<版本號碼\>*997.xsd 和 X12\\*\<版本號碼\>_TA1.xsd。 這些結構描述的目標命名空間是 http://schemas.microsoft.com/BizTalk/EDI/X12/2006 。  

 EDIFACT 支援兩階段通知模式。 第一階段通知是交換接收，這是使用 CONTRL 結構描述的三個區段所建構。 此技術通知會報告標頭驗證結果。 第二階段通知則會使用 CONTRL 結構描述的其餘區段。 此結構描述的命名慣例是 EFACT_<VERSION\<版本號碼\>_CONTRL.xsd。 此結構描述的目標命名空間是 http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006 。  

## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md)   
 [BizTalk Server 如何傳送 EDI 訊息](../core/how-biztalk-server-sends-edi-messages.md)
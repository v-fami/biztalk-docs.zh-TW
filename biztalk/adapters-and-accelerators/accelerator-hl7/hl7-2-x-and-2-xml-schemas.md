---
title: "HL7 2.X 和 2.XML 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, schema types
- HL7-encoded messages
- 2.X schemas
- schemas, HL7 organization
- BTAHL7, HL7 schemas
- HL7, 2.XML schemas
- Update2XMLSchema tool
- schemas, common schemas
- 2.X schemas, about 2.X schemas
- 2.X schemas, compatibility
- 2.XML schemas, compatibility
- messages, HL7-encoded messages
- HL7 Schema Selector
- schemas, 2.XML schemas
- 2.XML schemas
- 2.XML schemas, about 2.XML schemas
- HL7, 2.X schemas
- schemas, compatibility
- common schemas
- schemas, 2.X schemas
ms.assetid: 02532d72-1948-48d8-a8ef-6b5a814eb573
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eec467f644919427fa6a3bc65264284f35ae650
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-2x-and-2xml-schemas"></a>HL7 2.X 和 2.XML 結構描述
HL7 組織發行的結構描述的兩個集合： HL7 2.X 結構描述，用於 HL7 編碼訊息和 HL7 2.XML 結構描述，用於 XML 編碼訊息。  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]適用於原生 HL7 2.X 結構描述。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]安裝程式載入 HL7 2.X 結構描述檔案到\<*磁碟機*>: \program files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for HL7\Templates\Schemas\2.X。 如此一來，HL7 2.X 結構描述位於 HL7 結構描述選取器。 在中執行 HL7 結構描述選取器[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  
  
 BTAHL7 搭配 HL7 2.XML 結構描述，BTAHL7 安裝程式不會載入 HL7 2.XML 結構描述與 BTAHL7 程式檔案，但您有修改，才能使用 BTAHL7 HL7 2.XML 結構描述的部份。 若要讓它們可供 HL7 結構描述選取器中並進行必要的修改，從 HL7 組織的網站，下載 2.XML 結構描述，然後執行**Update2XMLSchema**工具 (如需詳細資訊，請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md))。 視需要對使用此工具會修改 HL7 2.XML 結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，然後將它們放置\<*磁碟機*>: \program files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 >Accelerator for HL7\Templates\Schemas。  
  
 每個結構描述的集合包含一系列的版本。 HL7 2.X 即時的結構描述版本包含透過 2.5 2.1 (如需詳細資訊，請參閱[HL7 版本](../../adapters-and-accelerators/accelerator-hl7/hl7-versions.md))。 HL72。XML 結構描述版本包含 2.3.1、 2.4 和 2.5。 HL7 2.X 結構描述版本為回溯相容。 HL7 2.XML 結構描述版本不提供回溯相容。  
  
> [!NOTE]
>  因為無法回溯 2.XML 2.4 版與 2.XML 的 2.3.1 相容，可能會發生錯誤如果您部署 2.4 版本 2.XML 結構描述，然後送出符合 2.3.1 訊息執行個體版本。 若要修正此問題，您可能需要建立不同的目標命名空間來處理 2.3.1 訊息。  
  
 當您建立多部分 HL7 2.X 訊息，您必須設定的內文部分的類型為特定結構描述。 如果沒有的話，序列化程式將會拒絕該訊息。  
  
 下表描述結構描述與其 BTAHL7 適用於兩種基本類型。  
  
|結構描述類型|Description|  
|-----------------|-----------------|  
|HL7FF – ER7 編碼 (2.X) 結構描述|BTAHL7 提供 HL7 2.X 衍生自 HL7 存取資料庫的結構描述包括：<br /><br /> -一組根據版本、 訊息類型或事件的所有特定結構描述<br />-區段、 資料類型、 資料表、 標頭，以及認可 (Ack) 的通用結構描述<br /><br /> BTAHL7 支援下列結構描述範本：<br /><br /> -V2.1<br />-V2.2<br />-V2.3<br />-V2.3.1<br />-V2.4<br />-2.5 版<br /><br /> BTAHL7 安裝程式安裝 V2。中的結構描述 x \<*磁碟機*> \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7\Templates\Schemas。|  
|HL7XML – 2.XML 編碼方式|BTAHL7 支援下列結構描述：<br /><br /> -V2.3.1<br />-V2.4<br />-2.5 版<br /><br /> BTAHL7 安裝程式不會安裝 2.XML 結構描述。 若要安裝它們並修改這些工作與 BizTalk 編輯器，請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)。|  
  
## <a name="common-schemas"></a>通用結構描述  
 BTAHL7 使用 HL7 結構描述特有的訊息類型來建立和驗證該訊息類型的執行個體的本文。 它也會使用常見的結構描述，除了特定的結構描述。 BTAHL7 使用常見 HL7 結構描述驗證 HL7 訊息標頭和通知。 這些檔案會 MSH_25_GLO_DEF.xsd 標頭和 ACK_24_GLO_DEF 通知。  
  
 BTAHL7 也會使用通用的結構描述來驗證資料型別、 區段和資料表值。 這些結構描述特有的 HL7 標準的每個版本。 比方說，V2.2 訊息的一般結構描述為 datatype_22.xsd、 segments_22.xsd 和 tablevalues_22.xsd。 BTAHL7 會使用這些結構描述來驗證資料型別、 區段和資料表值的所有 V2.2 訊息。  
  
## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)
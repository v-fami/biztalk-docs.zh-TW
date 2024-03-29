---
title: HL7 2.X 和 2.xml 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69dc39b3f61dbb564fc3ef128405b8721633dd2d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994183"
---
# <a name="hl7-2x-and-2xml-schemas"></a>HL7 2.X 和 2.xml 結構描述
HL7 組織發行的結構描述的兩個集合： HL7 2.X 結構描述，用於 HL7 編碼訊息，以及 HL7 2.xml 結構描述，用於 XML 編碼訊息。  

 Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]適用於原生 HL7 2.X 結構描述。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 設定載入 HL7 2.X 結構描述檔案，放進\<*磁碟機*\>: \program files\\Microsoft BizTalk\<版本\>HL7\Templates\Schemas\2.X 的加速器。 如此一來，HL7 2.X 結構描述位於 HL7 結構描述選取器。 HL7 結構描述選取器以 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。  

 BTAHL7 搭配 HL7 2.xml 結構描述，BTAHL7 安裝程式不會載入 HL7 2.xml 結構描述以 BTAHL7 program files 中，但您必須修改一些 HL7 2.xml 結構描述，才能使用 BTAHL7。 若要讓它們可供 HL7 結構描述選取器中，並進行必要的修改，下載 2.xml 結構描述從 HL7 組織網站，然後執行**Update2XMLSchema**工具 (如需詳細資訊，請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md))。 視需要對使用，此工具會修改 HL7 2.xml 結構描述[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，然後將其放置\<*磁碟機*\>: \program files\\Microsoft BizTalk\<版本\>HL7\Templates\Schemas 的加速器。  

 這些結構描述集合的每一個都包含一系列的版本。 HL7 2.X 即時的結構描述版本包含透過 2.5 2.1 (如需詳細資訊，請參閱 < [HL7 版本](../../adapters-and-accelerators/accelerator-hl7/hl7-versions.md))。 HL72。XML 結構描述版本包括 2.3.1、 2.4 及 2.5。 HL7 2.X 結構描述版本是為了與舊版相容。 HL7 2.xml XML 結構描述版本不是為了與舊版相容。  

> [!NOTE]
>  因為 2.4 版 2.XML 不是為了與舊版 2.XML 的 2.3.1 與符合規範，可能會發生錯誤如果您部署 2.4 版本 2.XML 結構描述，然後提交符合 2.3.1 訊息執行個體版本。 若要修正此問題，您可能需要建立不同的目標命名空間來處理 2.3.1 訊息。  

 當您建立多部分 HL7 2.X 訊息，您必須設定的內文部分的型別特定的結構描述。 如果沒有，則序列化程式將會拒絕該訊息。  

 下表描述結構描述與其 BTAHL7 適用於兩種基本的類型。  


|            結構描述類型            |                                                                                                                                                                                                                                                                                                   描述                                                                                                                                                                                                                                                                                                    |
|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| HL7FF – ER7 編碼 (2.X) 結構描述 | BTAHL7 提供 HL7 2.X 結構描述衍生自 HL7 Access 資料庫，包括：<br /><br /> -一組根據版本、 訊息類型或事件的所有特定結構描述<br />-區段、 資料類型、 資料表、 標頭和通知 (Ack) 通用結構描述<br /><br /> BTAHL7 支援下列結構描述的範本：<br /><br /> -V2.1<br />-V2.2<br />-V2.3<br />-V2.3.1<br />-V2.4<br />-V2.5<br /><br /> BTAHL7 安裝程式安裝 V2。X 中的結構描述\<*磁碟機*\>\Program Files\\Microsoft BizTalk Accelerator for HL7\Templates\Schemas。 |
|      HL7XML – 2.使用 XML 編碼方式      |                                                                                                                                            BTAHL7 支援下列結構描述：<br /><br /> -V2.3.1<br />-V2.4<br />-V2.5<br /><br /> BTAHL7 安裝程式不會安裝 2.xml 結構描述。 若要安裝它們並加以修改以使用 BizTalk 編輯器中，請參閱[Update2XMLSchema 工具](../../adapters-and-accelerators/accelerator-hl7/update2xmlschema-tool.md)。                                                                                                                                            |

## <a name="common-schemas"></a>通用結構描述  
 BTAHL7 會使用 HL7 結構描述特有的訊息類型來建立和驗證該訊息類型的執行個體的本文。 它也會使用通用的結構描述，除了特定的結構描述。 BTAHL7 會使用常見 HL7 結構描述來驗證 HL7 訊息標頭和通知。 這些檔案會通知的標頭和 ACK_24_GLO_DEF MSH_25_GLO_DEF.xsd。  

 BTAHL7 也會使用常見的結構描述來驗證資料型別、 區段和資料表值。 這些結構描述特有的 HL7 標準的每個版本。 比方說，V2.2 訊息的一般結構描述是 datatype_22.xsd、 segments_22.xsd 和 tablevalues_22.xsd。 BTAHL7 會使用這些結構描述來驗證資料類型、 區段和 V2.2 的所有訊息的資料表值。  

## <a name="see-also"></a>另請參閱  
 [訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)
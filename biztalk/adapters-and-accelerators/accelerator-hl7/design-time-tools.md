---
title: 設計階段工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Adapter Framework
- BTAHL7, tools
- Starter Project
- Pipeline Designer
- BizTalk Editor
- Visual Studio Starter Project
- BizTalk Mapper
- design-time tools
- Orchestration Designer
ms.assetid: 709bd782-d2ad-49be-ba33-e957eba2a0cc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d60cf2a64863a842bb974fcce2d4217f9b8105f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997439"
---
# <a name="design-time-tools"></a>設計階段工具
開發人員在 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 必須使用 BizTalk Server 內建的設計階段工具組。 這些工具已整合到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 如需詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具，請參閱 MicrosoftBizTalk Server 說明。  
  
## <a name="biztalk-editor"></a>BizTalk Editor (BizTalk 編輯器)  
 您可以使用 BizTalk 編輯器來管理 HL7 XSD 結構描述。 您可以使用下列支援的結構描述範本 （以 XSD 檔案） 的開發您的解決方案：  
  
-   HL7: 2.1 （包括 37 事件）  
  
-   HL7: 2.2 （包含 56 事件）  
  
-   HL7: 2.3 （包括 182 的事件）  
  
-   HL7: 2.3.1 （包括 189 事件）  
  
-   HL7: 2.4 （包括 288 事件）  
  
-   HL7: 2.5 （包括大約有 390 的結構描述）  
  
-   HL7: 2.（V2.3.1 和 2.4 包括大約 450 的結構描述） 的 XML  
  
## <a name="biztalk-mapper"></a>BizTalk Mapper (BizTalk 對應工具)  
 使用「BizTalk 對應工具」可以建立和自訂定義資料轉換的對應。 對應的輸入和輸出的轉換的情況下，您在使用 BizTalk 對應工具[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]訊息類型。  
  
## <a name="biztalk-orchestration-designer"></a>BizTalk 協調流程設計師  
 「BizTalk 協調流程設計師」可以設計和實作商務程序。  
  
## <a name="biztalk-pipeline-designer"></a>BizTalk 管線設計師  
 您可以使用 BizTalk 管線設計師來建立及設定定義管線並處理步驟的連結。 管線會將處理分成各個階段，並決定執行每個類別的工作順序。  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 提供接收和傳輸管線取得所有支援的 HL7 版本。 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 提供具有自訂 HL7 剖析器和解譯器/組合器元件的管線範本。  
  
## <a name="biztalk-adapter-framework"></a>BizTalk 配接器架構  
 「BizTalk 配接器架構」可以搭配端點配接器一起使用，以便與交易夥伴及應用程式進行整合。  
  
## <a name="visual-studio-starter-project"></a>Visual Studio 入門專案  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] 包含[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]入門專案，您可以使用快速入門 HL7 解決方案實作。 將入門專案包含下列專案：  
  
- **空**[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**專案**。     不包含任何結構描述。  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V2XCommon 專案**。 包含標頭和通知結構描述。  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V21Common 專案**。 包含適用於 HL7 2.1 版通用結構描述。  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V22Common 專案**。 包含針對 HL7 2.2 版通用結構描述。  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V23Common 專案**。 包含 HL7 2.3 版通用結構描述。  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V231Common 專案**。 包含針對 HL7 2.3.1 版通用結構描述。  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V24Common 專案**。 包含為 HL7 2.4 版通用結構描述。  
  
- BTAHL7**V25Common 專案**。 包含針對 HL7 2.5 版通用結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [工具和功能](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md)   
 [分析工具](../../adapters-and-accelerators/accelerator-hl7/analysis-tools2.md)
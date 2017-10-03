---
title: "開發探查管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], probing
- IProbeMessage interface
- pipeline interfaces, IProbeMessage
ms.assetid: c3da467d-5270-4c7f-9c38-ce9989bf1b63
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8081c31fc781cd2d1cbc291587f358376a033d66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-probing-pipeline-component"></a>開發探查管線元件
可實作任何管線元件 （一般、 組合或解譯）`IProbeMessage`介面必須支援訊息探查功能。 探查元件會用於具有管線階段**FirstMatch**執行模式。 在這種階段中，BizTalk 傳訊引擎會提供訊息的開頭部分給元件，以確定該元件是否可識別訊息的格式。 若元件可識別格式，則會傳送完整的訊息給此元件進行處理。  
  
 **IProbeMessage**介面會公開單一方法**探查**，可讓元件能夠檢查訊息的開頭部分。 其傳回值則決定此元件是否已執行。 下列步驟簡要說明 BizTalk 傳訊引擎如何執行需要識別的階段。  
  
1.  若階段中未包含任何元件，則不會執行此階段，而且會將訊息傳送給後續階段進行處理。  
  
2.  檢查元件是否實作**IProbeMessage**介面。 若未實作，傳訊引擎會叫用元件。 完成階段處理，並將訊息傳送到下一個階段。  
  
3.  **探查**叫用方法。 如果傳回值是**True**，元件會執行。 接著便完成階段處理，並將訊息傳送到下一個階段。  
  
4.  傳訊引擎會取得此階段中的下一個元件。 如果已經沒有其他元件，而且尚未執行任何元作，則會產生管線處理已經失敗的錯誤。 如果已經沒有其他元件，但已經執行至少一個元件，則處理已完成。  
  
 如果階段不需要辨識 (例如，執行模式是**所有**)，傳訊引擎會叫用元件而不先查詢**IProbeMessage**介面及呼叫**探查**方法。  
  
## <a name="see-also"></a>另請參閱  
 [開發一般管線元件](../core/developing-a-general-pipeline-component.md)   
 [開發組合管線元件](../core/developing-an-assembling-pipeline-component.md)   
 [開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)   
 [報告管線元件錯誤](../core/reporting-errors-from-pipeline-components.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [部署管線元件](../core/deploying-pipeline-components.md)
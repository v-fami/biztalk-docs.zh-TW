---
title: 處理解譯器管線元件中的編碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], encoding
- pipeline components [custom], disassembling
ms.assetid: 33420357-421f-4ad0-8eee-d445376676db
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bcbfb8f86847668436fae04db7bee1703dfb60ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246702"
---
# <a name="handling-encoding-in-a-disassembler-pipeline-component"></a>處理解譯器管線元件中的編碼
確定您的自訂解譯器元件使用下列其中一種格式為輸出文件編碼：  
  
-   UTF-8  
  
-   UTF-16  
  
-   UTF-32  
  
-   UTF-16LE  
  
-   UTF-16BE  
  
 協調流程引擎可能無法處理具有其他編碼格式的文件。  
  
 .NET Framework 不支援 UTF-32LE 和 UTF-32BE，若要使用這些格式，您必須建立自訂編碼實作。  
  
## <a name="see-also"></a>另請參閱  
 [開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)
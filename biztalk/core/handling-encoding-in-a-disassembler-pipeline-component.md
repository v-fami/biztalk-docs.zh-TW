---
title: 在解譯器管線元件中處理編碼 |Microsoft Docs
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
ms.openlocfilehash: 596161cd2ccf5d4f9a492bbdd23cd8f6f22c5c2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995231"
---
# <a name="handling-encoding-in-a-disassembler-pipeline-component"></a>在解譯器管線元件中處理編碼
確定您的自訂解譯器元件使用下列其中一種格式為輸出文件編碼：  
  
- UTF-8  
  
- UTF-16  
  
- UTF-32  
  
- UTF-16LE  
  
- UTF-16BE  
  
  協調流程引擎可能無法處理具有其他編碼格式的文件。  
  
  .NET Framework 不支援 UTF-32LE 和 UTF-32BE，若要使用這些格式，您必須建立自訂編碼實作。  
  
## <a name="see-also"></a>另請參閱  
 [開發解譯管線元件](../core/developing-a-disassembling-pipeline-component.md)
---
title: 對應元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file types, maps
- BizTalk Mapper, output
- maps, file type
- maps, file contents
- BizTalk Mapper, file type
- maps, components
ms.assetid: be438d21-80a8-49d8-bd08-d85618ab23de
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1590ad1450453602b4dd5f25b2d52a4364787af
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996767"
---
# <a name="map-components"></a>對應元件
對應檔 (具有 .btm 副檔名) 會儲存對應的大部分元件。 檔案中儲存的項目包含：  
  
- 來源與目的結構描述的參考  
  
- 連結，包括連結屬性  
  
- 運算質及其屬性，例如輸入參數  
  
- 其他屬性，例如與格線和對應本身相關聯的屬性。  
  
  雖然 BizTalk 對應工具可將 .btm 檔案中的對應編譯至可延伸樣式表轉換 (XSLT) 檔案中，但 XSLT 並不是檔案的一部分。 只有當您在編譯專案或在驗證對應時，BizTalk 對應工具才能為對應產生 XSLT。 BizTalk 對應工具會將 XSLT 封裝為專案組件的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)
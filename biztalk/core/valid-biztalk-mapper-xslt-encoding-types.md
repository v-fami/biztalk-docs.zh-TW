---
title: 有效的 BizTalk 對應工具 XSLT 編碼類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- grid properties
- Code Page property
- XSLT Encoding property [grid pages]
- Schema node
- XSLT, encoding types [BizTalk Mapper]
- BizTalk Mapper, XSLT encoding
ms.assetid: 922b46cb-7bc8-4267-bf52-e5f0262b8da1
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 874e30f6d1cb56880dc9b15cce9c815305430871
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012335"
---
# <a name="valid-biztalk-mapper-xslt-encoding-types"></a>有效的 BizTalk 對應工具 XSLT 編碼類型
BizTalk 對應工具支援不同的可延伸樣式表語言轉換 (XSLT) 編碼類型。 您使用**XSLT 編碼**格線屬性，以設定的 XSLT 編碼您偏好的類型。 下列清單顯示相關聯的下拉式清單中可用的編碼格式**XSLT 編碼**格線屬性：  
  
- 無  
  
- 阿拉伯文 (windows-1256)  
  
- 波羅的海文 (windows-1257)  
  
- 中歐語系 (windows-1250)  
  
- 簡體中文 (GB18030)  
  
- Cyrilice (windows-1251)  
  
- 希臘文 (windows-1253)  
  
- 希伯來文 (windows-1255)  
  
- 日文 (Shift_JIS)  
  
- 韓文 (ks_c_5601-1987)  
  
- Little Endian Unicode (UTF-16)  
  
- 簡體中文 (GBK)  
  
- Thajština (windows-874)  
  
- 繁體中文 (Big5)  
  
- 土耳其文 (windows-1254)  
  
- UTF-8  
  
- 越南文 (windows-1258)  
  
- 西歐 (windows-1252)  
  
  若您在此清單中找不到想使用的編碼，您可以輸入不同的編碼值。 請確定您提供的值有效，因為 BizTalk 對應工具不會測試該值。  
  
> [!NOTE]
>  **字碼頁**屬性**結構描述**節點在對應中定義的結構描述，您使用的編碼格式。 若要設定**字碼頁**屬性，在 [BizTalk 編輯器] 中開啟結構描述，並指定值**字碼頁**屬性。  
  
## <a name="see-also"></a>另請參閱  
 [對應](../core/maps.md)   
 [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)
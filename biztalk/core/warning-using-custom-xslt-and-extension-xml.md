---
title: 警告-使用自訂 XSLT 與延伸模組 XML |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.warning.usingCustomXsltAndExtensionXML
ms.assetid: b86da5fb-6435-4e3b-89b6-d9d036b5152b
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90644aec738345e3a36286cc62aaa7a355e04348
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="warning---using-custom-xslt-and-extension-xml"></a>警告-使用自訂 XSLT 與延伸模組 XML
**錯誤碼**  
  
 btm1035  
  
 **說明**  
  
 值覆寫存在**自訂 XSLT 路徑**和**自訂延伸模組 XML**屬性會控制此對應中，完全略過任何對應所產生的輸出執行個體訊息指定來源和目的地結構描述之間。 若您是刻意這樣做，則可以略過此警告。  
  
 這是有效的其中一個案例是使用 BizTalk 對應工具產生對應的基本 XSLT，修改此 XSLT 以手動方式以符合特殊需求，然後指定已修改的檔案做為值**自訂 XSLT 路徑**屬性，藉此覆寫基本 XSLT，在後續對應作業。  
  
 **使用者動作**  
  
 如果您不想要覆寫此對應所指定的對應，會移除覆寫值**自訂 XSLT 路徑**屬性和**自訂延伸模組 XML**適當的屬性。
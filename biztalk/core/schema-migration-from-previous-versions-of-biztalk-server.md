---
title: 從舊版 BizTalk Server 移轉結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bdc86401-2002-40b8-a919-2c00cf42b557
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54b9dba1ee759cd33f7f3db44553684c27b57d10
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022460"
---
# <a name="schema-migration-from-previous-versions-of-biztalk-server"></a>從舊版 BizTalk Server 移轉結構描述
此版本的 BizTalk Server 使用「XML 結構描述定義」(XSD) 語言來表示訊息結構描述，舊版則使用 XML-Data Reduced (XDR) 語法來表示訊息結構描述。 若要從舊版的 BizTalk Server 進行移轉，必須將您的結構描述轉換成使用 XSD 而非 XDR。  
  
 您必須執行下列工作，才能將 BizTalk 結構描述從 XDR 語法轉換成 XSD 語法：  
  
- 變更結構描述檔案 from.xdr to.xsd 的延伸模組。  
  
- 將重新命名的結構描述新增至適當的 BizTalk 專案。  
  
- 在 [BizTalk 編輯器] 中開啟結構描述，將重新命名的結構描述由 XDR 轉換成 XSD。  
  
- 儲存該結構描述，以確認永久轉換。  
  
  如需如何執行這些步驟的詳細資訊，請參閱[如何移轉至 XSD 結構描述的 XDR 結構描述](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關於結構描述](../core/about-schemas.md)   
 [如何將 XDR 結構描述移轉至 XSD 結構描述](../core/how-to-migrate-xdr-schemas-to-xsd-schemas.md)   
 [移轉一般檔案記錄](../core/migrating-flat-file-records.md)
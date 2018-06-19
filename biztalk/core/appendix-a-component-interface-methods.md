---
title: 附錄 a： 元件介面方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- component interfaces, methods
- methods, component interfaces
- component interface methods
ms.assetid: c8377589-fbdf-4287-b822-53263a00381d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61cb5b87cb063f22c889291b8eff3b2be50d64a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230102"
---
# <a name="appendix-a-component-interface-methods"></a>附錄 a： 元件介面方法
Microsoft BizTalk Adapter for PeopleSoft Enterprise 有針對元件介面提供標準方法。  
  
> [!NOTE]
>  前版方法中的 `interactiveMode` 參數有助於偵錯對後端的呼叫 (`Create/CreateEx`、`Update/UpdateEx` 和 `DeleteOnly`)。 對後端之 *Ex 呼叫中的每個項目都是分別進行呼叫，因此您會清楚知道哪個項目執行失敗。 沒有效能降低當您使用\*Ex 方法由於每個屬性的項目都會收到不同的呼叫。 您可以使用開發\*Ex 方法後再切換至主要方法 (例如， `Create`) 生產環境。 您也可以使用在實際執行偵錯參數，使用此方法之間切換， \*Ex 方法。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [CreateEx 方法](../core/createex-method.md)  
  
-   [DeleteOnly 方法](../core/deleteonly-method.md)  
  
-   [Find 方法](../core/find-method.md)  
  
-   [Get 方法](../core/get-method.md)  
  
-   [UpdateEx 方法](../core/updateex-method.md)  
  
-   [元件介面使用者定義方法](../core/component-interface-user-defined-methods.md)  
  
-   [Effective Date 屬性](../core/effective-date-properties.md)
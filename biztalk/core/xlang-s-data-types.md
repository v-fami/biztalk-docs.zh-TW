---
title: XLANG 的資料型別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, expressions
- Orchestration Designer, managing data
- Orchestration Designer, variables
- orchestrations, variables
- Orchestration Designer, expressions
ms.assetid: 5b08aaa6-1533-4bac-a76d-f9162e39bf4f
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c21ed77c5fdd56485514d17ed75e921c63a56212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290438"
---
# <a name="xlang-s-data-types"></a>XLANG 的資料型別
XLANG/s 會定義標準數值型別，這些型別為其 C# 對應型別的反映， 這些包括**布林**，**位元組**， **Char**，**十進位**， **Double**， **Int16**， **Int32**， **Int64**， **SByte**，**單一**，**字串**， **UInt16**， **UInt32**，和**UInt64**。 XLANG/s 支援單一維度陣列，但不支援陣列常值。  
  
 XLANG/s 也支援許多種訊息處理方式。 訊息可以基於結構描述、.NET 類別、Web 訊息類型 (WSDL) 或複雜的訊息類型。 XLANG/s 支援下列複雜的資料型別：  
  
-   **messagetype。** 此資料型別定義其定義的資料元素，以 XSD 為基礎的訊息組合為多部分訊息類型和方法訊息類型 （符合的類別或介面的方法簽章格式的訊息）。  
  
-   **連接埠類型。** 這種資料型別會定義該類型之連接埠執行個體可執行的連接埠作業集合。  
  
-   **correlationsettype。** 這種資料型別會定義將用於任何相互關聯集合變數執行個體中的資料。 相互關聯集合資料是一種路由機制，可確保系統中移動的訊息會分派至正確的執行中商務程序執行個體。 例如，如果採購單傳送至交易夥伴進行處理，在採購單傳回時，必須叫用正確對應的商務程序執行個體。  
  
-   **servicelinktype。** 此資料型別定義的一組**porttype**形成邏輯一致的商務程序中使用的連接埠群組的值。 使用服務連結是一項功能強大的機制，允許在執行階段對連接埠群組進行動態指派。 這可讓您定義一個可用於與多個交易夥伴互動的商務程序。  
  
## <a name="see-also"></a>另請參閱  
 [XLANG s 陳述式](../core/xlang-s-statements.md)   
 [XLANG 的變數和運算子](../core/xlang-s-variables-and-operators.md)   
 [XLANG 的運算式](../core/xlang-s-expressions.md)   
 [XLANG s 保留字](../core/xlang-s-reserved-words.md)   
 [XLANG-s 至 BPEL4WS 型別轉換](../core/xlang-s-to-bpel4ws-type-conversions.md)
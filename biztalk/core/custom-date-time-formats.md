---
title: 自訂日期時間格式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5efbec4-3138-44d7-bc76-f9c21547e1d5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4bf6a5027accb6a1ac5f9c28ba07b548953c873
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985055"
---
# <a name="custom-date-time-formats"></a>自訂日期時間格式

## <a name="overview"></a>概觀
您建立一般檔案結構描述使用的一般檔案格式，基於其舊有來源，會使用不符合 ISO 8601 格式的日期和時間格式。 因此，您要建立一般檔案結構描述，而且您設定**資料型別**屬性**欄位項目**或是**欄位屬性**節點的其中一個 XML 結構描述定義 （XSD) 語言基本資料型別**xs: datetime**， **xs: time**，或**xs: date**，您可以使用**自訂日期/時間格式**屬性來指定替代格式的日期或時間值。  

> [!NOTE]
>  在訊息方塊中的儲存體截斷時間值中的**xs: datetime**並**xs: time**的毫秒以下的項目。 轉換成 .NET日期/時間資料型別時，也可能發生類似的遺失有效位數的情況。  

 一般檔案解譯器會轉譯成其對等 XML 這類欄位時，值格式化**自訂日期/時間格式**屬性會用來允許一般檔案日期/時間格式轉換成它的 ISO 8601 相容對等項目。 同樣地，當一般檔案組合器會轉譯為相等的一般檔案的 ISO 8601 相容日期/時間值，指定的格式字串中**自訂日期/時間格式**屬性用以建構適當的日期 /一般檔案中預期的時間格式。  

> [!NOTE]
>  依照預設，與 XSD 日期和時間資料型別對應的值 (有數個) 都必須符合 ISO 8601 格式。 簡單地說，日期以**YYYY 為 YYYY-MM-DD**和小時會表示為**hh: mm:** 使用 24 小時制標記法。 當它們同時出現時，在以"T"字元分隔日期和時間值： **YYYY:MM:DDThh:mm:ss**。  

 您可以設定**自訂日期/時間格式**屬性幾乎任何時間和日期的格式，儒略日除外。 下拉式清單提供各種選擇，但您可以選擇自行輸入不同的格式。 日期和時間格式使用 Common Language Runtime (CLR) **DateTime**設備。 唯一的例外是單一字元 d、m 或 M 開頭會自動加上百分比符號 (%)，以產生對應的 DateTime 值單一項目。 自訂日期/時間格式允許的分隔符號為虛線 (-)、斜線及句號 (.)。 如需詳細資訊**DateTime**格式，在 Visual Studio 文件集合中搜尋"Datetimeformatinfo"。  

## <a name="see-also"></a>另請參閱  
- [欄位考量](../core/field-considerations.md)   
- **資料類型 （所有結構描述的節點屬性）** 和**自訂日期時間格式 （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]

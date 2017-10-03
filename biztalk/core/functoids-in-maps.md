---
title: "在對應中的運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids
- functoids, about functoids
- functoid types, Record Count
- functoid types, Looping
- Looping functoids
- functoids, categories
- functoid types, Addition
- Record Count functoids
ms.assetid: 10ee8b62-cb20-4d26-9d86-b6564f30c297
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976af2faed27e6cae8a57d9c7c83308d0519d81d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="functoids-in-maps"></a>對應中的運算質
BizTalk 對應工具支援來源結構描述的記錄和欄位與目的結構描述中的複雜結構化轉換，從記錄和欄位。 運算質透過使用預先定義的公式和特定值來執行計算，稱為引數。 會根據記錄和欄位的指定順序執行這些計算。  
  
 透過從工具箱選取運算質，將它拖曳到格線頁，再將它連結到來源結構描述和目的結構描述中的節點，您可以同時新增資料、修改日期或時間資訊、串連資料，或是執行其他作業。 例如，**加法**運算質會將值加入和**記錄計數**運算質會傳回執行個體訊息中的迴圈記錄總計數。 您可以在 [工具箱] 中找到的運算質類別包括： 進階、 轉換、 累計、 資料庫、 日期 / 時間、 邏輯、 數學、 科學，以及字串。  
  
> [!NOTE]
>  除了資料庫運算質之外，所有運算質皆為內嵌 C#。  
  
> [!NOTE]
>  目的結構描述節點接受只能有一個輸入例外的運算質**迴圈**運算質。  
  
 本節主題描述如何移轉舊版本 BizTalk Server 的運算質、什麼是運算質、它們的用途，以及如何使用它們。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [運算質類別](../core/functoid-categories.md)  
  
-   [運算質輸入參數](../core/functoid-input-parameters.md)  
  
-   [基本運算質](../core/basic-functoids.md)  
  
-   [進階運算質](../core/advanced-functoids.md)  
  
-   [串聯運算質](../core/cascading-functoids.md)  
  
-   [運算質屬性](../core/functoid-properties.md)  
  
-   [移轉運算質](../core/migrating-functoids.md)
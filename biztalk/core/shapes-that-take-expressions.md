---
title: "採用運算式的圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Expression Editor, shapes
- Decide shape [Orchestration Designer], expressions
- Message Assignment shape [Orchestration Designer], expressions
- Filter Expression property
- Listen shape [Orchestration Designer], expressions
- Delay shape [Orchestration Designer], expressions
- shapes, expressions
- Receive shape [Orchestration Designer], expressions
- Loop shape [Orchestration Designer], expressions
- Rule shape [Orchestration Designer]
ms.assetid: 0d27f711-ff7c-422b-b231-aa3c9a42ed0c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e78ada2c69205a0201c4bae9f3c7fa5b0656fa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="shapes-that-take-expressions"></a>採用運算式的圖形
數個圖形在協調流程設計師中，包括**決定**和**迴圈**，使用布林運算式來控制分支的格式規則。 其他的圖形則使用其他目的運算式。 您可以使用 BizTalk 運算式編輯器，為這些圖形建立或編輯運算式。  
  
 下表摘要了使用協調流程設計師中運算式的圖形，並列出這些運算式的有效資料型別。  
  
|形狀圖|運算式使用的描述|有效的運算式資料型別|  
|-----------|-----------------------------------|---------------------------------|  
|**決定**|**決定**圖形包含**規則**圖形，它會使用布林值運算式。|布林|  
|**接收**|**接收**圖形，將啟動屬性設定為 True 使用**篩選條件運算式**屬性來篩選內送訊息。 此屬性中的運算式必須評估為布林值，其值會決定是否接受內送訊息。<br /><br /> **篩選條件運算式**對話方塊用來建立篩選條件運算式。|布林|  
|**迴圈**|A**迴圈**圖形需要**規則**形狀，接著必須包含布林運算式。|布林|  
|**規則**|**規則**圖形 （以 「 分支 」 圖形方式顯示於 「 處理區域） 是包含布林值運算式和其他 （複雜） 圖形中用來管理分支的簡單圖形。|布林|  
|**接聽**|每個分支**接聽**圖形包含，最少，請**接收**圖形，僅針對篩選條件運算式中使用布林運算式 (請參閱的項目**接收**)或**延遲**圖形，它會使用**System.DateTime**物件或**System.TimeSpan**物件。|布林值、System.DateTime、System.TimeSpan|  
|**延遲**|中使用的運算式**延遲**圖形必須評估為**System.DateTime**物件，以表示期限，或**System.TimeSpan**物件來表示持續時間。|System.DateTime、System.TimeSpan|  
|**訊息指派**|中的運算式**訊息指派**圖形會將值指派至訊息。 一般來說，雖然會指派訊息，但是指派的值可以是任何型別。|任意|  
|**運算式**|**運算式**圖形可讓您輸入您的協調流程中所選擇的運算式。 例如，您可以進行 .NET 呼叫以執行外部程式，或是只管理協調流程變數的值。|任意|  
  
## <a name="in-this-section"></a>本節內容  
 [如何使用運算式圖形](../core/how-to-use-expression-shape.md)  
  
## <a name="see-also"></a>另請參閱  
 [運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)   
 [建構訊息](../core/constructing-messages.md)   
 [設定流程控制圖形](../core/configuring-flow-control-shapes.md)
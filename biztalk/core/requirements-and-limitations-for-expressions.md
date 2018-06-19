---
title: 運算式的需求與限制 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Expression Editor, about Expression Editor
- Expression Editor, requirements
- Orchestration Designer, Expression Editor
- Expression Editor, limitations
- Expression Editor
- Expression Editor, Orchestration Designer
ms.assetid: 1e0353d3-c2f3-4c10-86e3-8620e62dd0d5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd819850f62d47c640753e843325c9851da177b5
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22268382"
---
# <a name="requirements-and-limitations-for-expressions"></a>運算式的需求和限制
協調流程設計師中的 [BizTalk 運算式編輯器] 是標準的 Visual Studio 文字編輯器，這表示它會提供 IntelliSense。 您可以使用 [BizTalk 運算式編輯器] 輸入文字格式的運算式。  
  
 使用文字方塊，以文字格式輸入單一運算式。 運算式可以跨越多行，但必須以一個分號結尾。  
  
 以下列出在 [BizTalk 運算式編輯器] 中使用運算式時的限制：  
  
-   不支援複合指派，例如 "+="、"-=" 或 "*="。  
  
-   不支援在陳述式中使用一個以上的設定運算子。  
  
-   不支援在 "if" 或 "while" 述詞中使用指派。  
  
-   不支援遞增和遞減。 例如，"++" 和 "--"。  
  
-   對於訊息部分，允許在公用方法、巢狀型別、靜態資料欄位、有 Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute 註解的唯讀 .NET 屬性、所有公用資料欄位和非唯讀 .NET 屬性上使用成員存取。  
  
-   不支援索引子或參數化 .NET 屬性。  
  
-   不支援委派和事件。  
  
-   不支援泛型。  
  
-   不支援流程控制語法，例如 "foreach"、"for"、"do-while"、"break" 和 "continue"。  
  
-   不支援三元運算。 例如，"?:"。  
  
-   您可以在「運算式」圖形中加入註解，但是「運算式」圖形必須包含至少一個陳述式。  
  
-   不支援陣列。  
  
-   將「運算式」圖形置入「建構訊息」圖形時，您不可以加入任何控制流程。 例如，"if-then-else" 或 "while"。  
  
-   所有有效的運算式陳述式，格式應為：  
  
    -   Dotted-name = expression;  
  
    -   Dotted-name = expression;  
  
 雖然使用 [BizTalk 運算式編輯器]，可以輕鬆快速地輸入複雜的運算式，但是您不可以用它輸入任意數量的程式碼。 究其原因，是為了讓商務程序的程式碼與其實作程式碼分開。
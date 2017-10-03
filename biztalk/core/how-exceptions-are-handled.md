---
title: "例外狀況處理的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, handlers
- scopes, errors
- errors, scopes
- handlers [adapters], errors
ms.assetid: 30b88d8a-8737-4700-b856-1b49fdf6b6d0
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 004e4f29bcfc292edb33bae816a52b588a89771c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-exceptions-are-handled"></a>如何處理例外狀況
當例外狀況在某個範圍內發生時，在該範圍中執行的每個邏輯執行緒都會停止。 執行階段引擎便會嘗試尋找適當例外狀況的例外狀況處理常式。  
  
 如果找到的例外狀況處理常式符合特定型別或是其基底型別之一，便會將控制傳遞到該處理常式並執行其程式碼。  
  
> [!NOTE]
>  例外狀況類型必須衍生自**System.Exception**。  
  
 例外狀況處理常式是循序的，也就是說，這些處理常式會依順序接受檢查，以決定它們是否能夠處理特定的例外狀況。 為正常運作，例外狀況處理常式必須在放置時，讓這些處理更為特定類型的例外狀況處理常式先出現，後面則跟著處理較為一般類型的處理常式。 如此您才能確定特定類型的例外狀況會由適當的處理常式所處理，而非設計用來處理基底型別的處理常式。  
  
 如果例外狀況處理常式正常完成，控制便會傳遞到周圍的範圍中。 如果在周圍的範圍中沒有擲回例外狀況，協調流程便會繼續執行。 如果例外狀況處理常式以擲回陳述式結束，除非您指定要擲回不同的例外狀況，否則會在要對其行動的周圍範圍再度擲回原始的例外狀況。  
  
 如果找不到例外狀況處理常式，便會執行預設的例外狀況處理常式。 範圍的預設例外狀況處理常式會呼叫任何巢狀交易的補償，然後再度擲回例外狀況。 如果您撰寫自己的例外狀況處理常式，即可選擇不要傳送例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況](../core/exceptions.md)
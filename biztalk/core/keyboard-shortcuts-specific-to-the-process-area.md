---
title: 鍵盤快速鍵特有的 「 處理區域 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard shortcuts, Orchestration Designer
- Orchestration Designer, keyboard shortcuts
ms.assetid: d993d341-99f2-4788-b1f3-6a8b911e5278
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba60b23c6c8719789e8de6903dbb538fa5088b08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262062"
---
# <a name="keyboard-shortcuts-specific-to-the-process-area"></a>「 處理區域的專用鍵盤快速鍵
下表描述 [處理區域] 中可用的鍵盤巡覽方式，[處理區域] 是設計介面的中央區域，用來定義協調流程的處理流程。  
  
|索引鍵|效果|  
|---------|------------|  
|DOWN ARROW|將選取範圍移至下一個連接線或下面的圖形。 若圖形連接至下面的數個分支 (如同在 [決定] 圖形的情況)，則選取範圍會移至最左邊分支的第一個圖形。<br /><br /> 若選取範圍在協調流程的 [結束] 圖形上，則按下此按鍵會沒有作用，因為其下方已經沒有其他圖形。|  
|向上鍵|將選取範圍移至下一個連接線或上面的圖形。 若圖形連接至上面的數個分支，則選取範圍會移至最左邊分支的最後一個圖形。<br /><br /> 按下此按鍵會沒有任何作用**啟動**選取圖形。|  
|向左鍵|若選取範圍是在 [傳送] 或 [接收] 圖形，且圖形連接至某個連接埠：<br /><br /> -若圖形具有連至 [左連接埠介面] 中連接埠連接器，焦點和選取範圍會轉移至圖形的連接埠連接器。<br />-若圖形具有連至 [右連接埠介面] 中，按下此按鍵會沒有任何作用。<br />-如果圖形有沒有連接埠連接器，巡覽作業和任何其他圖形一樣。<br /><br /> 對於其他圖形 (或未連接至連接埠的 [傳送] 或 [接收] 圖形)：<br /><br /> -如果選取範圍位於分支中，且含有圖形的最新分支中，左邊分支左邊分支上將選取範圍移至最接近的圖形。<br />-索引鍵有協調流程中其他位置沒有作用。|  
|向右鍵|與向左鍵相同，但方向相反。|  
|HOME|將選取範圍變更至從協調流程之 [開始] 圖形連過來的連接器。|  
|END|將選取範圍變更至連至協調流程之 [結束] 圖形的連接器。|  
|NUM LOCK + -|摺疊選取的複雜圖形。|  
|NUM LOCK + +|展開選取的複雜圖形。|  
|NUM LOCK + *|展開選取的複雜圖形，及其擁有的任何子複雜圖形。|  
  
## <a name="see-also"></a>另請參閱  
 [協調流程設計工具鍵盤快速鍵](../core/orchestration-designer-keyboard-shortcuts.md)
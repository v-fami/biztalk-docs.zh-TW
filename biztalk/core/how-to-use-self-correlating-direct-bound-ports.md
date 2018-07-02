---
title: 如何使用自我相互關聯直接繫結連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: feb651fa-3e35-4598-b229-335448f6919c
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaad102db33b4967c89cb78f944b93a688e4c213
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982319"
---
# <a name="how-to-use-self-correlating-direct-bound-ports"></a>如何使用自我相互關聯的直接繫結連接埠
自我相互關聯的直接繫結連接埠是自我參考的。 這代表自我相互關聯的直接繫結連接埠會提供資訊，供協調流程將訊息傳回包含它的協調流程。 使用自我相互關聯的直接繫結時，協調流程引擎會在協調流程執行個體特定的訊息上產生相互關聯 Token。 這樣就可以將訊息傳回特定的協調流程執行個體，而不需使用相互關聯集合。  
  
 例如，您可以在其中建立接收的自我相互關聯直接繫結的連接埠在協調流程 A 中的指定**直接**如**連接埠繫結**，然後選取**自我相互關聯**連接埠組態精靈 中。 然後在「協調流程 B」中，將連接埠宣告為「協調流程 A」所定義之相同連接埠類型的傳送埠協調流程參數。若要執行這項作業，請進行下列步驟：  
  
1. 在 [協調流程檢視] 視窗中，以滑鼠右鍵按一下**協調流程參數**，然後按一下**新的連接埠參數**。  
  
2. 在 [屬性] 視窗中，如**通訊方向**，選取**傳送**，以及**連接埠類型**，協調流程 a 中所定義，請選取相同的連接埠類型  
  
   這個宣告會建立邏輯傳送埠協調流程設計師中的連接埠介面上。 協調流程 A 呼叫協調流程 B 」: 使用**啟動協調流程**圖形並將新的連接埠做為參數，以及其他協調流程的參數，傳遞到協調流程 b 的協調流程 B，然後執行其商務邏輯及傳送新的連接埠傳遞給它的訊息。 該訊息會傳送到「協調流程 A」執行個體的接收端自我相互關聯直接繫結連接埠 (「協調流程 A」即為啟動「協調流程 B」的協調流程)。  
  
   雖然上述事件的順序也都適用於**呼叫的協調流程**圖形，它才有意義時使用**啟動協調流程**圖形。 這是因為使用時**呼叫的協調流程**圖形，參考所傳遞的連接埠。 兩個協調流程都必須具有相同的連接埠極性。 因此，您從一個協調流程進行傳遞時所使用的連接埠通訊方向，必須與所呼叫之協調流程中的連接埠參考方向相同。 不過，使用時**啟動協調流程**圖形，就會產生非同步的協調流程具現化，而且不得有**Out**或是**Ref**參數;因此，自我相互關聯直接繫結連接埠可以讓協調流程以回應執行個體化該協調流程執行個體。  
  
   如何使用自我相互關聯直接繫結的連接埠的範例，請參閱 SDK 範例 「 實作 Scatter 和 Gather 模式 」，網址[ http://go.microsoft.com/fwlink/?LinkId=73703 ](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 MessageBox 直接繫結連接埠](../core/how-to-use-messagebox-direct-bound-ports.md)   
 [如何使用夥伴協調流程直接繫結連接埠](../core/how-to-use-partner-orchestration-direct-bound-ports.md)
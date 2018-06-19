---
title: 在協調流程中的持續性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, persistence
- persistence
- BizTalk Server Orchestration Engine
ms.assetid: 2f79d294-f7df-4d84-ba76-50618506b6c6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af73db551ced1206ac316f0ba15b8c90a7d5053f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264590"
---
# <a name="persistence-in-orchestrations"></a>協調流程持續性
協調流程引擎會在不同的持續點儲存協調流程執行個體的整個狀態，讓協調流程執行個體能夠解除凍結。 除了訊息和變數以外，狀態還包括可能在協調流程中使用的任何 .NET 架構元件。 引擎將狀態存放在下列持續點：  
  
-   交易式範圍的結尾 (不可部分完成或長執行)。  
  
-   在偵錯中斷點  
  
-   在透過「啟動協調流程」圖形執行其他協調流程時  
  
-   在「傳送」圖形 (不可部分完成的交易除外)  
  
-   當協調流程執行個體被擱置時  
  
-   當系統在控制的情況下關機時  
  
-   當引擎決定要凍結時  
  
-   當協調流程執行個體完成時  
  
 引擎會最佳化持續點的數目，因為這些會耗費許多資源，在處理大的訊息大小時尤其如此。 如以下兩個協調流程執行個體所示，在將「傳送圖形」置於不可部分完成範圍的協調流程中，引擎會決定在交易式範圍結尾與協調流程結尾之間具有單一的持續點。 在另一個協調流程中，則會有兩個持續點，一個用於第一個「傳送」圖形，第二個則用於「傳送」圖形加上協調流程的結尾。  
  
 **協調流程持續性**  
  
 ![協調流程持續性](../core/media/bts-trans-orch-fig2.gif "BTS_Trans_Orch_Fig2")  
  
 您在協調流程中使用的任何 .NET 架構物件，除非是在不可部分完成範圍中叫用，或是物件沒有狀態而且只能透過靜態方法叫用，否則無論是直接或是間接，都必須標記為可序列化。 **System.Xml.XmlDocument**是特殊案例，而且不需要將會標示為可序列化，不論範圍的交易屬性。  
  
 如何執行特殊處理**System.Xml.XmlDocument**運作：  
  
 當使用者定義變數**X**型別的**T**，其中**T**是**System.Xml.XmlDocument**或類別衍生自**System.Xml.XmlDocument**則編譯器會將**X**為可序列化的物件。  
  
 當序列化**X**，執行階段會保留下列資訊項目: （a） 的實際型別**Tr**物件的**X**參考 （b) **OuterXml**文件的字串。  
  
 在還原序列化**X**，執行階段將建立的執行個體**Tr** （這裡假設未採用任何參數的建構函式），並將呼叫**LoadXml**提供將儲存的執行個體**OuterXml。X**則會設為指向新建立的執行個體的**Tr**。  
  
## <a name="see-also"></a>另請參閱  
 [Transactions](../core/transactions.md)
---
title: 如何設定延遲圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer], configuring
- Delay shape [Orchestration Designer]
- Delay shape [Orchestration Designer], timeouts
- Delay shape [Orchestration Designer], about Delay shape
- configuring [Orchestration Designer], Delay shapes
ms.assetid: 727be28d-932a-41d5-af3f-3ee6f7129a17
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b76448398facd3af7f3b9712491f9895ffb406d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22248334"
---
# <a name="how-to-configure-the-delay-shape"></a>如何設定延遲圖形
![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")  
延遲圖形  
  
 有兩種方式來指定的逾時 **延遲**:  
  
-   您可以使用 **System.DateTime**, ，而導致您的協調流程暫停，直到指定的日期和時間為止。  
  
     System.DateTime.UtcNow.AddSeconds(60)  
  
    > [!NOTE]
    >  延遲必須以表示在國際標準時間 (UTC) 使用時 **DateTime**。  
  
-   您可以使用 **System.TimeSpan**, ，而導致您的協調流程暫停指定的時間長度。  
  
     System.TimeSpan(0, 1, 0)  
  
 如果您 **延遲** 圖形位於 **接聽** 圖形，您不需要在運算式結尾處加上分號。  
  
 如需詳細資訊 **System.DateTime** 和 **System.TimeSpan**, ，請參閱 「 DateTime 結構 」 和 「 TimeSpan 結構 」 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 結合的集合。  
  
> [!NOTE]
>  中的多電腦安裝環境其中 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 SQL Server 安裝在不同的電腦， **延遲** 圖形可能比預期時間因為提早結束 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 機器不同步。  
  
> [!NOTE]
>  在逾時指定在負荷條件下 **延遲** 圖形可能會發生晚於您指定的內容。 這是因為負荷條件下的執行緒匱乏現象。  
  
### <a name="to-configure-a-delay-shape"></a>若要設定延遲圖形  
  
1.  如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下 **延遲** 圖形，並按一下 **編輯延遲**, ，或在 屬性 視窗中，按一下  **省略** (**...**) 按鈕 **運算式** 屬性。  
  
2.  在 [BizTalk 運算式編輯器] 中，建立一個運算式會傳回 **System.DateTime** 物件或 **System.TimeSpan** 物件。 如需詳細資訊，請參閱[運算式的需求與限制](../core/requirements-and-limitations-for-expressions.md)。
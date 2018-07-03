---
title: 如何設定延遲圖形 |Microsoft Docs
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
ms.openlocfilehash: 7c00e002418dac53295828a4cbed632a6de0c235
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993647"
---
# <a name="how-to-configure-the-delay-shape"></a>如何設定延遲圖形
![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")  
延遲圖形  
  
 有兩種方式來指定的逾時**延遲**:  
  
- 您可以使用**System.DateTime**，因而導致協調流程暫停到指定的日期和時間為止。  
  
   System.DateTime.UtcNow.AddSeconds(60)  
  
  > [!NOTE]
  >  延遲必須以表示以 Coordinated Universal Time (UTC) 使用時**DateTime**。  
  
- 您可以使用**System.TimeSpan**，這樣會使您的協調流程暫停指定的時間長度。  
  
   System.TimeSpan(0, 1, 0)  
  
  如果您**延遲**圖形位於**接聽**圖形，您不需要在運算式結尾加上分號。  
  
  如需詳細資訊**System.DateTime**並**System.TimeSpan**，請參閱中的 < DateTime 結構 > 和 < TimeSpan 結構 >[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]組合集合。  
  
> [!NOTE]
>  中的多電腦安裝環境所在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 安裝在不同的電腦**延遲**圖形可能比預期時間因為提早結束[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]機器是未同步處理。  
> 
> [!NOTE]
>  在負荷條件下指定中的逾時**延遲**圖形可能比您指定的內容。 這是因為負荷條件下的執行緒匱乏現象。  
  
### <a name="to-configure-a-delay-shape"></a>若要設定延遲圖形  
  
1.  如果看不到 BizTalk 運算式編輯器，以滑鼠右鍵按一下**延遲**圖形，然後按一下**編輯延遲**，或在 屬性 視窗中，按一下 **省略符號**(**...**) 按鈕**運算式**屬性。  
  
2.  在 [BizTalk 運算式編輯器] 中，建立該運算式會傳回**System.DateTime**物件或**System.TimeSpan**物件。 如需詳細資訊，請參閱 <<c0> [ 運算式的需求和限制](../core/requirements-and-limitations-for-expressions.md)。
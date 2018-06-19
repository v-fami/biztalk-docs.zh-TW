---
title: 平行群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Parallel Task shape [Orchestration Designer], concurrent receive tasks
- messages, convoys
- correlation sets, concurrent receive tasks
- correlation sets, Parallel Task shape [Orchestration Designer]
- orchestrations, messages
- messages, correlating to orchestrations
ms.assetid: 036aa8c0-f49c-47f0-ac1e-6c667bca3811
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c6993aa3c5dd47cb5b554dd8ab2080020ebb80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264838"
---
# <a name="parallel-convoys"></a>平行群組
平行群組可讓多個單一訊息聯結在一起，以達成所需的結果。 一組相關的訊息會依任何順序抵達，但 BizTalk Server 必須收到所有的訊息，才能開始處理。  
  
 例如，當醫院接受新病患時，醫院會要求病患提供多項資訊，包括保險資訊、過去就醫記錄和連絡資訊。 有幾種不同的人會收集此資訊，包括保險專員、護士和服務台人員。 有數個不同系統會處理此資訊。 收集和提交此資訊的工作不保證一定會按照正常的順序進行。 例如，資訊收集者可能忙著招呼其他病患、醫療記錄部門的動作可能落後預定時間，或者保險系統可能運作不正常。 我們必須在病患的就醫期間內，有系統地組織病患的這些資訊。 如此才能保證病患受到妥善的醫療照顧，而且收到正確的帳單。  
  
 上述的案例便是需要平行群組訊息處理的商務案例。 商務需求會衍生出一種規定，迫使醫院必須在收到三種不同訊息之後，才接受病患。 這三種訊息即是「保險」、「病歷」和「病患」訊息。 這些屬於病患的任何一則訊息都可能是最先抵達的訊息，因此會產生競爭條件。 若要解決這個問題，請三個**接收**圖形放進**平行動作**形狀和每個接收標示為 Activate = True。 這讓三個訊息中的任何一個都可以啟動協調流程。 協調流程執行個體會等到另外兩個訊息抵達之後，再繼續執行進一步的處理。  
  
## <a name="implementing-parallel-convoys"></a>實作平行群組  
 您可以使用 BizTalk Server 中的「平行相互關聯的接收」傳訊設計模式來實作平行群組。 平行相互關聯接收相互關聯接收陳述式中的兩個或多個分支**平行動作**圖形。 如果會在一項以上的平行工作中初始化相互關聯，則每個相互關聯接收也必須初始化一組完全相同的相互關聯。 這項工作會接收相互關聯的訊息會先執行實際的初始化、 和中的其他工作上執行驗證**平行動作**協調流程中的圖形。  
  
 平行群組實作的範例，請參閱 SDK 範例 「 平行群組 」，在[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。  
  
## <a name="see-also"></a>另請參閱  
 [使用群組實例](../core/working-with-convoy-scenarios.md)   
 [循序群組](../core/sequential-convoys.md)
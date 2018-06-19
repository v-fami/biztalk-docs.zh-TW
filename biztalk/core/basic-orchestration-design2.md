---
title: 基本協調流程 Design2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, design
ms.assetid: fcdcb232-6a8f-41f3-b863-3b9e2cda28e3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 713d37d2736b8fac4563b098572dd9e49a3fd634
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230614"
---
# <a name="basic-orchestration-design"></a>基本協調流程設計
當您建立基本協調流程時，在您的協調流程的接收埠收到 XML。 XML 傳送到後端系統上，進行處理。 在後端系統中，可能會發生例外狀況，無法停止協調流程。 所產生的例外狀況提供未完成的協調流程的資訊。  
  
 當錯誤發生時，會暫停呼叫。 在事件檢視器記錄，您可以檢視該錯誤以及失敗的原因。  
  
 若要防止協調流程進入擱置狀態並要重新導向該錯誤，您可以建立 CatchExpression。 若要捕捉後端，產生的例外狀況，並協助找出問題的原因，您可以使用 「 範圍 」 圖形在協調流程中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 例外狀況處理](../core/using-biztalk-server-exception-handling3.md)
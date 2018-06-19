---
title: 處理中斷點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, breakpoints
- Orchestration Debugger, suspended orchestrations
- Orchestration Debugger, Message Flow view
- Orchestration Debugger, service options
- Message Flow view [Orchestration Debugger]
ms.assetid: aad1a2b0-d705-49cd-85f7-b0ab2e473bcc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60e9cee77f105b132438e621651ee90c0090c1be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289206"
---
# <a name="working-with-breakpoints"></a>處理中斷點
您可以將中斷點附加到擱置的協調流程，或在類別上設定中斷點，以設定中斷點。  
  
> [!NOTE]
>  當您解除部署組件時，資料庫會保留該組件的追蹤選項與中斷點資訊。 若您之後再次部署相同的組件，就會還原該組件的選項與中斷點資訊。  
  
### <a name="to-attach-to-a-suspended-orchestration"></a>附加到擱置的協調流程  
  
1.  使用擱置圖形選取自動擱置的協調流程，然後移至步驟 3。  
  
2.  重新整理檢視以檢查執行個體現在顯示為「已擱置」狀態。  
  
3.  按一下**在偵錯繼續**。  
  
     協調流程會於「在中斷點」狀態下繼續。 您現在可以互動方式進行偵錯。  
  
### <a name="to-switch-to-the-message-flow-view"></a>切換至 [訊息流程] 檢視  
  
-   以滑鼠右鍵按一下 [結果] 清單中的資料格，然後選取**訊息流程**從捷徑功能表。  
  
## <a name="see-also"></a>另請參閱  
 [使用協調流程偵錯工具檢視](../core/working-with-the-orchestration-debugger-view.md)
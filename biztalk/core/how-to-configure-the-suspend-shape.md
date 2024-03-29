---
title: 如何設定擱置圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Suspend shapes
- Suspend shape [Orchestration Designer], literal strings
- Suspend shape [Orchestration Designer], configuring
- Suspend shape [Orchestration Designer]
- atomic transactions, Suspend shape [Orchestration Designer]
- Suspend shape [Orchestration Designer], atomic transactions
- Suspend shape [Orchestration Designer], about Suspend shape
ms.assetid: 62fbb6d4-78d2-4671-84bb-909cbf6b0ec3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c846001b5a2b39a4e23e0d06ed56fb91c8863832
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248518"
---
# <a name="how-to-configure-the-suspend-shape"></a>如何設定擱置圖形
![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")  
擱置圖形  
  
 當協調流程執行個體遭到擱置時，便會記錄錯誤訊息。 您可以指定隨著這個錯誤顯示的訊息字串，以協助管理員診斷此狀況。  
  
 協調流程執行個體的所有狀態資訊都會被儲存起來，並在管理員繼續此協調流程執行個體時復原。  
  
> [!NOTE]
>  如果**暫停**圖形位於協調流程同步呼叫 (如同**呼叫**圖形) 由另一個協調流程，巢狀的執行個體和所有封閉式協調流程執行個體將暫止。  
  
> [!NOTE]
>  您不能放置**暫停**不可部分完成的交易內圖形。  
  
### <a name="to-configure-a-suspend-shape"></a>若要設定擱置圖形  
  
-   您可以使用**錯誤訊息**屬性來指定您想要的文字時記錄**暫停**遇到圖形。 此文字可能是常值字串或運算式評估為**System.String**。  
  
    > [!CAUTION]
    >  如果您輸入常值字串，就必須將其括在引號中。
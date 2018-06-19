---
title: 如何設定補償圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Compensate shape [Orchestration Designer], about Compensate shape
- Compensate shape [Orchestration Designer]
- compensations, Compensate shape [Orchestration Designer]
- configuring [Orchestration Designer], Compensate shape
- Compensate shape [Orchestration Designer], configuring
ms.assetid: 9f06289e-4d11-4864-9851-c210276865a7
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 059ac58d95d33234737033c00c4a6a2a36e256f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248278"
---
# <a name="how-to-configure-the-compensate-shape"></a>如何設定補償圖形
如果您在協調流程中使用巢狀的交易，您可以加入**補償**補償區塊或例外狀況區塊的交易範圍中的圖形。 如此可讓您的協調流程能明確地在巢狀交易執行補償。 指定您想要在補償的交易**補償**形狀和巢狀交易中的任何補償程式碼將會執行，提供已成功認可交易。  
  
> [!NOTE]
>  **補償**屬性指的是交易範圍的唯一識別碼，它不是指領域的名稱。  
  
 如果您想要補償一個以上的巢狀的交易，您將另一個**補償**每一筆交易的圖形。  
  
 否**補償**圖形時，需要有外部交易中沒有其他補償程式碼; 任何巢狀交易的補償程式碼將會自動執行。 **補償**圖形可讓您控制處理程序可讓您決定是否要補償巢狀的交易。  
  
### <a name="to-configure-a-compensate-shape"></a>若要設定補償圖形  
  
-   在 屬性 視窗中，選取 從呼叫的補償區塊**補償**下拉式清單。  
  
     此下拉式清單將會顯示可以補償的所有交易，其中包括目前交易以及目前交易的任何直接子交易。 如果您看不到您預期的交易，可能是因為與這些交易的關係所導致。  
  
    > [!NOTE]
    >  您無法從目前交易的主體內來補償目前的交易，  您可以從此交易的補償區塊或例外狀況區塊來補償它。  
  
     如果您選擇補償目前的交易，這表示將會叫用預設處理常式，而不是明確的補償區塊 (如果有的話)。 這是自動補償已成功完成之直接巢狀交易的一項機制。
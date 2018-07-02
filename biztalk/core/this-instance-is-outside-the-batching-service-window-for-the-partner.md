---
title: 這個執行個體是外部交易夥伴的批次處理服務視窗 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e420d75-11fd-4221-9d97-814ca6e48c81
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a741439b5d6691a3218811568087450f2008b0ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966479"
---
# <a name="this-instance-is-outside-the-batching-service-window-for-the-partner"></a>此執行個體在夥伴的 [批次處理服務] 視窗外
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                    批次引擎                                     |
|  符號名稱  |                              OutsideBatchingServiceWindow                              |
|  訊息文字   |          此執行個體在夥伴的 [批次處理服務] 視窗外          |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於批次處理協調流程的執行個體位在合作對象的啟動範圍之外，因此該執行個體無法啟動。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，開啟 [EDI 屬性] 的 [交換批次建立設定] 頁面的合作對象，並確定協調流程執行個體是在啟動範圍內。 如果沒有，請變更開始時間屬性，然後再按一下**啟動**。
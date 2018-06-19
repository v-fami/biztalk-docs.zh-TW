---
title: 這個執行個體為夥伴批次服務窗口之外 |Microsoft 文件
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
ms.openlocfilehash: e93e7e769a8f0e30b3753af690a69c5e6eaa9786
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278662"
---
# <a name="this-instance-is-outside-the-batching-service-window-for-the-partner"></a>此執行個體在夥伴的 [批次處理服務] 視窗外
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|OutsideBatchingServiceWindow|  
|訊息文字|此執行個體在夥伴的 [批次處理服務] 視窗外|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於批次處理協調流程的執行個體位在合作對象的啟動範圍之外，因此該執行個體無法啟動。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，開啟 交換批次建立設定 頁面的 EDI 屬性的合作對象，並確定協調流程執行個體是在啟動範圍內。 如果沒有，請變更的開始時間屬性，然後再按一下**啟動**。
---
title: TA1 區段功能群組後，仍找到 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3d090a-0916-4a0e-82dc-2c9af9f97683
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86e9ac6e1e0c3a3b76dbc144739f3a16fddd0d67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278518"
---
# <a name="ta1-segment-found-after-a-functional-group"></a>功能群組後，仍找到 TA1 區段
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|TA1FoundAfterFunctionalGroup|  
|訊息文字|功能群組後，仍找到 TA1 區段。 因此，訊息已被拒絕|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送通知因為通知所包含的功能群組，然後 TA1 區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，有的 TA1 通知會確認該交換不包含之前 TA1 區段中，功能群組，然後再重新傳送通知的寄件者。
---
title: 包含群組數目不相符 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d61ac17-92cd-4a5e-81e6-e2c6fc4085bb
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f02262012a5d02cebaf86fae5a4d19d9b5486d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263030"
---
# <a name="number-of-included-groups-do-not-match"></a>包括的群組數目不相符
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12Ta1InvalidNumberOfIncludedGroupsDescription|  
|訊息文字|包括的群組數目不相符|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示交換中的群組數目不等於交換結尾 （IEA01 欄位） 中的數字。 會發生這種情況時保留交換，並發生錯誤時暫停交換。 （錯誤訊息不張貼如果保留交換和交易集發生錯誤時，就會暫停，或是在交換分割。）  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定交換結尾 IEA01 欄位中的編號是相同的交換中的群組數目然後再重新傳送交換。
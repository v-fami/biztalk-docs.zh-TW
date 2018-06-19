---
title: 重複以上需要 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fec52b5b-e95f-479e-8922-dcf17dcefee7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cb8f9e324c9d09e09649719c98e3f684b0d81f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268222"
---
# <a name="repeats-more-than-required"></a>重複以上所需
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12FeRepeatsMoreThanRequiredDescription|  
|訊息文字|重複以上所需|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示區段中的 X12 交換的是內部或外部迴圈會重複多次的文件結構描述所要求。  
  
## <a name="user-action"></a>使用者動作  
 若要解決此錯誤，確定交換中迴圈內外的區段重複結構描述中所指定的次數，然後重新傳送交換。